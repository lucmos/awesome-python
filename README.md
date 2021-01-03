# Awesome Python
An **opinionated selection** of awesome python stuff.


- [Awesome Python](#awesome-python)
  - [Packages](#packages)
    - [benedict‑benedict](#benedictbenedict)
    - [DearPyGui](#dearpygui)
    - [einops](#einops)
    - [imageio](#imageio)
    - [loguru](#loguru)
    - [pendulum](#pendulum)
    - [PrettyErrors](#prettyerrors)
    - [pydantic](#pydantic)
    - [python-dotenv](#python-dotenv)
    - [python-fire](#python-fire)
    - [questionary](#questionary)
    - [rich](#rich)
    - [scikit-image](#scikit-image)
    - [sensor-sensor](#sensor-sensor)
    - [tqdm](#tqdm)
  - [Tools](#tools)
    - [black](#black)
    - [scalene](#scalene)


## Packages

### [benedict‑benedict](https://github.com/fabiocaccamo/python-benedict)
python‑benedict is a dict subclass with keylist/keypath support, I/O shortcuts (`base64`, `csv`, `json`, `pickle`, `plist`, `query-string`, `toml`, `xml`, `yaml`.) and many utilities... for humans, obviously.
```python
from benedict import benedict

# create a new empty instance
d = benedict()

# or cast an existing dict
d = benedict(existing_dict)

# or create from data source (filepath, url or data-string) in a supported format:
# Base64, CSV, JSON, TOML, XML, YAML, query-string
d = benedict('https://localhost:8000/data.json', format='json')

# or in a Django view
params = benedict(request.GET.items())
page = params.get_int('page', 1)
```

### [DearPyGui](https://github.com/hoffstadt/DearPyGui)
Dear PyGui is a simple to use (but powerful) Python GUI framework.

[![](https://github.com/hoffstadt/DearPyGui/raw/assets/linuxthemes.PNG?raw=true)](https://github.com/hoffstadt/DearPyGui)

### [einops](https://github.com/arogozhnikov/einops)
Flexible and powerful tensor operations for readable and reliable code.

[![](https://camo.githubusercontent.com/07b9f5bdffbe9d2ee878e4cba4bf0def4657e84b7c91bc830705e2f45ce3339d/687474703a2f2f61726f676f7a686e696b6f762e6769746875622e696f2f696d616765732f65696e6f70732f65696e6f70735f766964656f2e676966)](https://github.com/arogozhnikov/einops)


### [imageio](https://github.com/imageio/imageio)
Imageio is a Python library that provides an easy interface to read and write a wide range of image data, including animated images, video, volumetric data, and scientific formats.

```python
import imageio
im = imageio.imread('imageio:chelsea.png')  # read a standard image
im.shape  # im is a NumPy array
>> (300, 451, 3)
imageio.imwrite('~/chelsea-gray.jpg', im[:, :, 0])
```

### [loguru](https://github.com/Delgan/loguru)
Loguru is a library which aims to bring enjoyable logging in Python.

[![](https://raw.githubusercontent.com/Delgan/loguru/master/docs/_static/img/demo.gif)](https://github.com/Delgan/loguru)


### [pendulum](https://github.com/sdispater/pendulum)
Python datetimes made easy.

```python
>>> import pendulum

>>> now_in_paris = pendulum.now('Europe/Paris')
>>> now_in_paris
'2016-07-04T00:49:58.502116+02:00'

# Seamless timezone switching
>>> now_in_paris.in_timezone('UTC')
'2016-07-03T22:49:58.502116+00:00'

>>> tomorrow = pendulum.now().add(days=1)
>>> last_week = pendulum.now().subtract(weeks=1)

>>> past = pendulum.now().subtract(minutes=2)
>>> past.diff_for_humans()
>>> '2 minutes ago'

>>> delta = past - last_week
>>> delta.hours
23
>>> delta.in_words(locale='en')
'6 days 23 hours 58 minutes'

# Proper handling of datetime normalization
>>> pendulum.datetime(2013, 3, 31, 2, 30, tz='Europe/Paris')
'2013-03-31T03:30:00+02:00' # 2:30 does not exist (Skipped time)

# Proper handling of dst transitions
>>> just_before = pendulum.datetime(2013, 3, 31, 1, 59, 59, 999999, tz='Europe/Paris')
'2013-03-31T01:59:59.999999+01:00'
>>> just_before.add(microseconds=1)
'2013-03-31T03:00:00+02:00'
```


### [PrettyErrors](https://github.com/onelivesleft/PrettyErrors)
Prettifies Python exception output to make it legible.

[![](https://raw.githubusercontent.com/onelivesleft/PrettyErrors/master/example.png)](https://github.com/onelivesleft/PrettyErrors)


### [pydantic](https://github.com/samuelcolvin/pydantic)
Data validation and settings management using Python type hinting.

```python
from datetime import datetime
from typing import List, Optional
from pydantic import BaseModel

class User(BaseModel):
    id: int
    name = 'John Doe'
    signup_ts: Optional[datetime] = None
    friends: List[int] = []

external_data = {
    "id": "123",
    "signup_ts": "2017-06-01 12:22",
    "friends": [1, "2", b"3"],
}
user = User(**external_data)
print(user)
#> User id=123 name='John Doe' signup_ts=datetime.datetime(2017, 6, 1, 12, 22) friends=[1, 2, 3]
print(user.id)
#> 123
```

### [python-dotenv](https://github.com/theskumar/python-dotenv)
Python-dotenv reads key-value pairs from a `.env` file and can set them as environment variables. It helps in the development of applications following the [12-factor](http://12factor.net/) principles.

```python
from dotenv import load_dotenv

load_dotenv()  # take environment variables from .env.

# Code of your application, which uses environment variables (e.g. from `os.environ` or
# `os.getenv`) as if they came from the actual environment.
```

### [python-fire](https://github.com/google/python-fire)
Python Fire is a library for automatically generating command line interfaces (CLIs) from absolutely any Python object.

```python
import fire

class Calculator(object):
  """A simple calculator class."""

  def double(self, number):
    return 2 * number

if __name__ == '__main__':
  fire.Fire(Calculator)
```

```bash
python calculator.py double 10  # 20
python calculator.py double --number=15  # 30
```

### [questionary](https://github.com/tmbo/questionary)
Questionary is a Python library for effortlessly building pretty command line interfaces

[![](https://raw.githubusercontent.com/tmbo/questionary/master/docs/images/example.gif)](https://github.com/tmbo/questionary)

```python
import questionary

questionary.text("What's your first name").ask()
questionary.password("What's your secret?").ask()
questionary.confirm("Are you amazed?").ask()

questionary.select(
    "What do you want to do?",
    choices=["Order a pizza", "Make a reservation", "Ask for opening hours"],
).ask()

questionary.rawselect(
    "What do you want to do?",
    choices=["Order a pizza", "Make a reservation", "Ask for opening hours"],
).ask()

questionary.checkbox(
    "Select toppings", choices=["foo", "bar", "bazz"]
).ask()

questionary.path("Path to the projects version file").ask()
```

### [rich](https://github.com/willmcgugan/rich)
Rich is a Python library for rich text and beautiful formatting in the terminal.

[![](https://github.com/willmcgugan/rich/raw/master/imgs/features.png)](https://github.com/willmcgugan/rich)

### [scikit-image](https://github.com/scikit-image/scikit-image)
`scikit-image` is an image processing Python package that works with `numpy` arrays.

[![](https://scikit-image.org/docs/stable/_images/sphx_glr_plot_structuring_elements_001.png)](https://github.com/scikit-image/scikit-image)

### [sensor-sensor](https://github.com/parrt/tensor-sensor)
Clarifying exceptions and visualizing tensor operations in deep learning code.

```python
import torch
W = torch.rand(d,n_neurons)
b = torch.rand(n_neurons,1)
X = torch.rand(n,d)
with tsensor.clarify():
    Y = W @ X.T + b
```
[![](https://camo.githubusercontent.com/c463ae4036bc1ec2df1e44b2312b1c2bbee27fca63b4cfb07b5de1273f0c13e2/68747470733a2f2f6578706c61696e65642e61692f74656e736f722d73656e736f722f696d616765732f6d6d2e737667)](https://github.com/parrt/tensor-sensor)

`Cause: @ on tensor operand W w/shape [764, 100] and operand X.T w/shape [764, 200]`

### [tqdm](https://github.com/tqdm/tqdm)
Instantly make your loops show a smart progress meter - just wrap any iterable with `tqdm(iterable)`, and you're done!

[![](https://raw.githubusercontent.com/tqdm/tqdm/master/images/tqdm.gif)](https://github.com/tqdm/tqdm)


## Tools

### [black](https://github.com/psf/black)
Black is the uncompromising Python code formatter.


### [scalene](https://github.com/emeryberger/scalene)
Scalene is a high-performance CPU and memory profiler for Python that does a number of things that other Python profilers do not and cannot do.

[![](https://github.com/emeryberger/scalene/blob/master/images/sample-profile-pystone.png?raw=true)](https://github.com/emeryberger/scalene)
