![status](https://travis-ci.org/jbn/IPlantUML.svg?branch=master)

## What is it?

This Python package defines a [PlantUML](http://plantuml.com) cell magic for IPython. It lets you generate UML diagrams as inline SVG in your notebook. I'll add embellishments as needed. But, for now, I just needed something that worked and existed as a package (in pypi).

I based my code on [Steven Burke](https://github.com/sberke)'s [plantuml](http://chickenbit.com/blog/2014/10/inline-plantuml-diagrams-in-ipython-notebook) gist.

Installation
------------

First, install IPlantuml with pip.

```bash
pip install iplantuml
```

Then, install plantuml. On Debian based system you can install plantuml package. Otherwise you can download `plantuml.jar` and copy it to
`/usr/local/bin/plantuml.jar`.

    sudo apt install plantuml

Alternatively you can set a custom path for plantuml.jar during installation

```bash
git clone https://github.com/jbn/IPlantUML.git
cd IPlantUML
python setup.py install iplantuml --jarpath /my/custom/path/plantuml.jar
```

Usage
-----

In Ipython, first,

```python
import iplantuml
```

then, create a cell like

```python
%%plantuml --jar

@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response
@enduml
```

The output will be the generated SVG UML diagram using the plantuml.jar on your local system. To utilise remote rendering on plantweb omit the `--jar` argument:

```python
%%plantuml

@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response
@enduml
```


By default, the magic removes the intermediate (`tmp.uml`) and target (`tmp.svg`) files. However, if you enter a name in the `%%plantuml` line, it retains both files of `$name.uml` and `$name.svg`. For example,

```python
%%plantuml auth

@startuml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response
@enduml
```

generates and retains `auth.uml` and `auth.svg`.
