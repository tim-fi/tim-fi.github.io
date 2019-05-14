# Welcome to my personal website

## `whoami`

My name is Tim Fischer, I'm a 21 year old software engineer and computer science bachelor student at the University of Tübingen. I live in south-western Germany, to more specific in the county of Böblingen, about 30 minutes south of Stuttgart and 20 mintues north of Tübingen. I work at my university in the work group [Methods of Machine Learning](https://www.wsi.uni-tuebingen.de/lehrstuehle/methoden-des-maschinellen-lernens/), and at a small company called [mecodia](https://mecodia.de/). At both I work as a full-stack webdeveloper.

## What else?

In my free time I do many things, for the most part I code around a bit, playing with some side projects from time to time. But the rest of the time I spend hanging out with some friends and doing gymnastics.

## Projects

### [Talks.Tue](https://github.com/talks-tue/talks.tue.flask)
This is the project I currently work on at my University. It is meant to be a small web-app for managing all the the talks that take place around the CS-department of the university and the [MPI for Inteligent System branch in Tübingen](https://is.tuebingen.mpg.de/).

### [dfb_predict](https://github.com/tim-fi/dfb_predict)
This was a graded group project from university, the jist of it was that we needed to develop an application to predict game in the DFB 1.Liga, the german football league. It encompased everything from data collection and processing, match prediction using stochastic methods, and UI development for an easy to use interface.

#### Images of the UI
![data management tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/001.png)
![prediction config tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/002.png)
![prediction result tab](https://raw.githubusercontent.com/tim-fi/dfb_predict/master/presentation/gui_imgs/003.png)

### [md_template](https://github.com/tim-fi/md_template)

#### Desciption
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
