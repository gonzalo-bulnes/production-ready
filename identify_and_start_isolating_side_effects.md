Identify side-effects and start isolating them
==============================================

General idea
------------

Things outside of your code that affect —or are affected by— the behaviour of your code are called side-effects of your code. _(Calling the former a side-effect may be a bit of a stretch but they both can be treated very similarly to our purposes.)_

Testing code with side-effects is trickier than testing code without side-effects and requires a different approach. Also,side-effects often mark the boundaries between your code and its dependencies. These are places where change might need to happen without notice.

It is then generally interesting to identify those areas of side-effects and start isolating them. There is a hierarchy here: the most important part is to have side-effects in mind, isolating them is nice but doesn't need to be taken too far at first.

How to identify side-effects?
-----------------------------

### Common examples

- **API calls**: their return values may change from one call to another and the calling code —our code— doesn't have control over that.
- **Files**: when a piece of code creates a file is called multiple times, it will typically create the file the first time, then do something different (e.g. nothing because the file is already there). The behaviour of our code then changes as a side-effect of external factors.
- **Anything random**: some code does something with a random or pseudo-random value? Well, it will do a different thing every time.

### Useful criteria

- Can I precisely predict the result of executing some code?
- If I were to execute the same code multiple times, would it always return the same values? (e.g. `sing_birthday_song('Alice', 44)` _vs_ `check_weather_outside()` or `roll_fancy_dice(12)`)

If the answer to any of those questions is "no", then there is likely a side-effect somewhere in the function. This is not an exhaustive list, but it should give you a rough idea.

How to start isolating side-effects?
------------------------------------

The idea behind "isolation" here is to separate the code with side-effects from the code without side effects.

For example, let's assume we have this function:

```python
# weather.py

def is_it_cold_now():
  current_weather = requests.get(WEATHER_SERVICE_URL).json() # ①
  current_temp = current_weather["temperature"] # ③④
  return current_temp < 70 # ②

is_it_cold_now()
# => true
```

Let's identify side-effects:

- ① Current weather can obviously change from one API call to another. It is a side-effect.
- ② This comparison should not change over time. However, there is an implicit assumption that `current_temp` in expressed in degrees Fahrenheit...
- ③ ...which at this point depends on the weather service API.
- ④ And since we're looking at what could change in the weather service API, nothing says that the temperature will always be called `"temperature"` or be nested at the first level of the JSON response.

----

Now let's isolate the side-effects, starting by making our assumptions explicit to break the dependency between ② (which should have no side-effects) and ③:

```python
# weather.py

def is_it_cold_now():
  current_weather = requests.get(WEATHER_SERVICE_URL).json() # unchanged
  current_temp = current_weather["temperature"] # unchanged
  current_temp_F = current_temp # the weather service uses the Fahrenheit scale ⑤
  return current_temp_F < 70 # ⑥

is_it_cold_now()
# => true if the weather and API haven't changed! >.<
```

- ⑤ Could change when the weather API changes.
- ⑥ Has no-side effects anymore. Let's take it out and test it separately!

----

```python
# weather.py

def is_it_cold_now():
  current_weather = requests.get(WEATHER_SERVICE_URL).json() # unchanged
  current_temp = current_weather["temperature"] # unchanged
  current_temp_F = current_temp # the weather service uses the Fahrenheit scale ⑤
  return is_cold(current_temp_F)

# ⑥
def is_cold(temperature_F):
  return temperature_F < 70

is_it_cold_now()
# => true
```

- ⑤ The assumption is now explicit.
- ⑥ Has no side-effects anymore and is easy to test (see test file below).

```python
# test_weather.py

import unittest

import weather # the name of the module/file above

class TestWeather(unittest.TestCase):

    def test_anything_below_70_is_cold(self):
        self.assertEqual(weather.is_cold(73), false, "expected 73 not to be cold")
        self.assertEqual(weather.is_cold(70), false, "expected 70 not to be cold")
        self.assertEqual(weather.is_cold(69), true, "expected 69 to be cold")
        self.assertEqual(weather.is_cold(54), true, "expected 54 to be cold")

if __name__ == '__main__':
    suite = unittest.TestLoader().loadTestsFromTestCase(TestWeather)
    unittest.TextTestRunner(verbosity=2).run(suite)

# run me with: python weather_test.py
```

----

The function `is_it_cold_now` still has parts that have side-effects and parts that don't, but at this point it doesn't do much and we could get rid of it altogether without compromising on readability:

```python
# weather.py

def get_current_temperature():
  """Returns the current temperature (°F) from a weather service."""
  current_weather = requests.get(WEATHER_SERVICE_URL).json() # ⑧
  return current_weather["temperature"] # ⑦

# ⑨
def is_cold(temperature_F):
  return temperature_F < 70

current_temperature = get_current_temperature()
is_cold(current_temperature)
# => true
```

- ⑦ Now that the function [documentation][docstring] (or name) makes explicit the dependency on the weather API and codifies the temperature unit, we can spare some explicitness. (YMMV, it's a readability trade-off.)
- ⑧ Note that this function encapsulates multiple side-effects at once. Is that okay? Since they are all somewhat related (weather/weather API) I'd say yes. From the point of view of our code they are both far away enough to look the same. In practice, the weather API is unlikely to change much. If it was to become the case, maybe making the conversion or temperature extraction explicit at that point would be a good idea. #iteration
- ⑨ Now the code is clearly divided between function with side-effects (that will require specific testing) and functions without side-effects, that are fully reliable because well-tested already. If anything breaks, we know where to look : )

  [docstring]: https://www.python.org/dev/peps/pep-0257/

### When to stop?

If the only thing that remains to test are the functions with side-effects, and those functions contain no side-effect-free logic, then most of the logic of our code is properly tested and reliable.

Of course, we may be making mistakes in how we fetch data from our weather API, but manual testing will cover that satisfactorily for some time and there are better things to do next if we have time to spare!

<br/>
<p align="right">— Next: <a href="./identify_data_structures.md">Identify data structures and namespaces</a></p>
