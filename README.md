# Welcome to my personal website

## `whoami`

My name is Tim Fischer, I'm a 21 software engineer and computer science bachelor student at the University of Tübingen. I live in south-western Germany, to more specific in the county of Böblingen, about 30 minutes aouth of Stuttgart and 20 mintues north of Tübingen. I work at my university in the work group [Methods of Machine Learning](https://www.wsi.uni-tuebingen.de/lehrstuehle/methoden-des-maschinellen-lernens/), and at a small company called [mecodia](https://mecodia.de/). At both I work as a full-stack webdeveloper.

## What else?

In my free time I do many things, for the most part I code around a bit playing with some side projects from time to time. But the rest of the time I spend hanging out with some friends and doing gymnastics.

## Projects

### [md_template](https://github.com/tim-fi/md_template)

#### Desciption
This is a simple formatting engine, made to work well with markdown and json as a datasource.

The whole thing started after a pen and paper session with some friend where we used an online tool for our character sheets. Exporting the datasheets was possible through the tool, but as we soon found out it only exported everything as a json-file. Of course I started coming up with some sensible ways to format the data into something more human-readable. And thus the first version of this was born.

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
