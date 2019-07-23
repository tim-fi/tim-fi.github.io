# Welcome to my personal website

## `whoami`

My name is Tim Fischer, I'm a 21 year old software engineer and computer science bachelor student at the University of Tübingen. I live in south-western Germany, to more specific in the county of Böblingen, about 30 minutes south of Stuttgart and 20 mintues north of Tübingen. I work at my university in the work group [Methods of Machine Learning](https://www.wsi.uni-tuebingen.de/lehrstuehle/methoden-des-maschinellen-lernens/), and at a small company called [mecodia](https://mecodia.de/). At both I work as a full-stack webdeveloper. In my free time I do many things, for the most part I code around a bit, playing with some side projects from time to time. But the rest of the time I spend hanging out with some friends and doing gymnastics.

## Projects

Most of the following projects and more can be found on [my private github profile](https://github.com/tim-fi).

### [ActFit](https://github.com/tim-fi/ActFit)
ActFit is a simple UI tool for fitting functions to data. It is my extended version of a project a friend of mine created, who initially wrote it, because he was annoyed at having to write the same code over and over again when he wanted to fit data. His version made use of matplotlib widgets, but I felt there was room for improvement using tkinter instead.

### [Talks.Tue](https://github.com/talks-tue/talks.tue.flask)
This is the project I currently work on at my University. It is meant to be a small web-app for managing all of the talks that take place around the CS-department of the university and the [MPI for Inteligent Systems branch in Tübingen](https://is.tuebingen.mpg.de/).

### [dfb_predict](https://github.com/tim-fi/dfb_predict)
This was a graded group project from university, the jist of it was that we needed to develop an application to predict game in the DFB 1.Liga, the german football league. It encompased everything from data collection and processing, match prediction using stochastic methods, and UI development for an easy to use interface.

#### Images of the UI
![data management tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/001.png)
![prediction config tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/002.png)
![prediction result tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/003.png)

### [swpatterns](https://github.com/tim-fi/swpatterns)
This library is a superset to the [pyCompose](#pycompose)-project which I started when I wanted to see if I could implement interfaces in python. It include such things as said interfaces, composition (of course extended with interfaces), and even a small implementation of matching-expressions.

### [pyCompose](https://github.com/tim-fi/pycompose)

#### Description
This is a simple little python-"_library_" that abstracts composition of objects and the forwarding of attributes/fields into an inheritable wrapper. This came to be after watching [Ariel Ortiz's 2019 PyCon talk](https://www.youtube.com/watch?v=YXiaWtc0cgE) in which he mentioned the [forwardable](https://github.com/5long/forwardable) library, the syntax of which I found to be unclear and a not to pretty.

#### Example
```python
from pycompose import Compose


class A:
    test1 = "123"

    def hello(self):
        print("A")

    def __repr__(self):
        return "<A>"


class B:
    test2 = "456"

    def hello(self):
        print("B")

    def __repr__(self):
        return "<B>"


class C(
    Compose(A, "test1", ("hello", "helloA")),
    Compose(B, "test2", ("hello", "helloB"), name="b_object"),
):
    ...


c = C()
print(c.test1 + c.test2)  # > 123456
c.helloA()                # > A
c.helloB()                # > B
print(c._a, c.b_object)   # > <A> <B>
```

### [md_template](https://github.com/tim-fi/md_template)

#### Description
This is a simple formatting engine, made to work well with markdown and json as a datasource.

The whole thing started after a pen and paper session with some friend where we used an online tool for our character sheets. Exporting the datasheets was possible through the tool, but as we soon found out it only exported everything as a json-file. Of course I started coming up with some sensible ways to format the data into something more human-readable. And thus the first version of this was born as part of my [scripts collection](#scripts).

The current project though is a an evolution of the original version. I was mostly fed up with the fact the the original had to parse the template file and build an AST everytime the formatter was run. To get around this I added a simple way to compile the generated AST into a static file thanks to python's own pickle module and the wonderfull extension built upon it called dill.

#### Example
##### Template file: `template.md`
{% raw %}
```md
# Test {{ name }}

{% for key, value in data.items() %}
## {{ key }}
{{ value }}
{% endfor %}
```
{% endraw %}

##### Data file: `data.json`
```javascript
{
  "name": "World",
  "data": {
    "Test 1": "abc",
    "Test 2": "def",
    "Test 3": "ghi",
  }
}
```

##### Commands
```sh
md_template compile template.md template.mdtemp
md_template apply template.mdtemp data.json out.md
```

##### Result: `out.md`
```md
# Test World

## Test 1
abc

## Test 2
def

## Test 3
ghi
```

### [scripts](https://github.com/tim-fi/scripts)
This is a small collection of scripts I've written, some times out of necessity and somes times thanks to procrastination before exams...

The scripts written include things like...
* ...`md_toc`, which adds a table of contents (TOC) to markdown files
* ...`md_template`, the orignal version of [md_template](#md_template)
* ...`weather`, a simple cli for fecthing weather data from [wttr.in](https://wttr.in)
