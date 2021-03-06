[![Language](https://img.shields.io/badge/language-python-blue.svg)](https://docs.python.org/3/)
[![Build Status](https://travis-ci.org/jtrejo13/matlab-interpreter.svg?branch=master)](https://travis-ci.org/jtrejo13/matlab-interpreter)
[![Codecov](https://img.shields.io/codecov/c/github/jtrejo13/matlab-interpreter.svg)](https://codecov.io/gh/jtrejo13/matlab-interpreter)

# MATLAB Interpreter

A (simplified) MATLAB language interpreter. 

### Table of Contents

- [About](#about)
- [Features](#features)
- [Set Up](#set-up)
- [Running the Interpreter](#running-the-interpreter)
- [Tools](#tools)
- [Versioning](#versioning)
- [Author](#author)
- [Acknowledgements](#acknowledgements)

## About

This interpreter directly executes instructions written in the MATLAB language. The interpreter was written in Python and it uses the following strategies for parsing and analyzing the statements in a MATLAB script:

1) Reads and 'tokenizes' the input source code
2) Parses the tokenized source code and produces an Abstract Syntax Tree (AST)
3) Traverses and interprets the AST, executing expressions as it moves along the tree

## Features

### Current Version (v1.0)

Currently, the main feature of the interpreter is the ability to evaluate a series of simple mathematical expressions (+, -, *, /) and assign the result to an identifier (or variable). The interpreter 'remembers' that variable by maintaining it in scope and is then able to evaluate future expressions referencing such variable. Finally, the interpreter is also able to ignore MATLAB-style comments (%). Below is an example:

#### Example Input
```matlab
radius = 1.5      % the radius
PI     = 3.14     % pi constant

% area of the circle
circle_area  = PI * (radius * radius)
```
#### Example Output
```matlab
radius=1.5
PI=3.14
circle_area=7.065
```

### TODO Work

* ~~Building a simple UI using wxPython~~ - **DONE**

* Adding basic function support:
  - Trigonometry: cos, sin, tan
  - Arithmetic: power, floor, mod, round, abs
  - Exponents: exp, log, sqrt

* Matrix support
  - Ex. `A = [1, 2, 3; 4, 5, 6; 7, 8, 9]`

## Set Up

Follow these instructions to get the project running on your local machine for development and testing

### Option 1: Virtual Environment

This option assumes python 3.5, pip, and make are installed in your machine.

1) Install the virtual environment library (virtualenv) via pip:

```bash
$ pip install virtualenv
```

2) Create a virtual environment for a project:

```bash
$ cd my_project_folder
$ virtualenv env
```

3) To begin using the virtual environment, it needs to be activated and the requirements need to be installed:

```bash
$ source env/bin/activate
$ pip install -r requirements.txt
```

### Option 2: Docker - Virtual Machine

1) Download and install [Docker](https://www.docker.com/community-edition#/download) on your machine

2) Pull the following image for the virtual machine:
```bash
$ docker pull gpdowning/python
```

3) Verify successful pull:
```bash
$ docker images

REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
gpdowning/python    latest              9e0a05a1bd40        7 days ago          783.1 MB
python              3.5.2               58528474c16a        2 weeks ago         683.2 MB
```

4) Run docker within project directory:
```bash
$ cd my_project_folder
$ pwd
$ my_project_folder_full_path
$ docker run -it -v my_project_folder_full_path:/usr/user_name -w /usr/user_name gpdowning/python
```

## Running the Interpreter

There are two ways to execute the interpreter:

### Command-line Interface

The interpreter can be launched in a command-line interface either on a stand alone GUI, or the terminal 

```bash
$ python3 app.py
```

### Running a script

A '.m' script can also be evaluated by the interpreter. For instance, the example script [RunInterpreter.in](https://github.com/jtrejo13/matlab-interpreter/blob/master/RunInterpreter.in) would be executed as follows:

```bash
$ python3 RunInterpreter.py < RunInterpreter.in
```

## Tools

This project uses the following Python software development tools:

* [Python 3](https://docs.python.org/3/) - The programming language
* [Make](https://www.gnu.org/software/make/) - Automated builds
* [Git](https://www.git-scm.com/) - Source control
* [Pylint](https://www.pylint.org/) - Code static analysis
* [unittest](https://docs.python.org/3.5/library/unittest.html) - Unit testing
* [coverage](https://pypi.python.org/pypi/coverage) - Code coverage
* [Pydoc](https://docs.python.org/3.4/library/pydoc.html) - Automated documentation
* [autopep8](https://pypi.python.org/pypi/autopep8) - Automated formatting
* [TravisCI](https://education.travis-ci.com/) - Continious integration
* [wxPython](https://www.wxpython.org/) - User Interface

## Versioning

For the versions available, see the repository [tags](https://github.com/jtrejo13/matlab-interpreter/releases). 

## Author

* **Juan Trejo**
  - [GitHub](https://github.com/jtrejo13)
  - [LinkedIn](https://www.linkedin.com/in/jtrejo13/)
  - [Home](https://jtrejo13.github.io/)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgements

* Inspired by [rspivak](https://github.com/rspivak) and his 'Let's Build a Simple Pascal Interpreter' [project](https://github.com/rspivak/lsbasi)
* The GUI and console 'shell' were based on the following libraries: [wx.py.interpreter.py](https://github.com/wxWidgets/wxPython/blob/master/wx/py/interpreter.py), [wx.py.shell.py](https://github.com/wxWidgets/wxPython/blob/master/wx/py/shell.py), and [code.py](https://svn.python.org/projects/python/trunk/Lib/code.py)
