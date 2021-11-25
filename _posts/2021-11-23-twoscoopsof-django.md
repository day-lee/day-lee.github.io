---
title:  "[Two Scoops of Django 3.x] 1. Coding Style"
excerpt: ""
share: false
categories:
  - Django
tags:
  - [Blog, Django]

toc: true
toc_sticky: true
published: true
 
date: 2021-11-23
last_modified_at: 2021-11-23
---
## 1. Readable code matters!
- variable names should be clear: no abbreviation
- Document classes and methods
- Repeated code into reusable ones
- Keep functions and methods short (script itself)

## 2. PEP 8
Official guide of Python
- 4 spaces for indentation
- 2 blank lines btw top-level function and class definitions
- 1 blank line btw method definitions inside a class 
  <br>Useful Tools - Black: code formatter, Flake8: checking code quality
- 79-character limit

## 3. Imports
Imports should be grouped as follows:
- Standard library imports (from os.path import abspath)
- Core Django imports  (from django.db import models)
- Related third-party 
- From your Local app (from app.models import ExampleModel)

## 4. Explicit Relative Imports
Benefits: easier to move, rename, and version control
> "a powerful tool for separating individual modules from being tightly coupled to the architecture around them"

- Absolute import: when importing from outside the current app
- Explicit Relative: importing from another module in current app


```
# Relative imports of the 'cones' package
from .models import WaffleCone
from .forms import WaffleConeForm

# absolute import from the 'core' package
from core.views import FoodMixin


class WaffleConeCreateView(FoodMixin, CreateView):
model = WaffleCone
form_class = WaffleConeForm

```

## 5. Avoid Using Import * 
Always be explicit to avoid unpredictable results.
Class name might overlap and overwrite the other classes.

- Using aliases to avoid name collisions.
```
from django.db.models import CharField as ModelCharField
```


## 6. Django Coding Style

### 1) Django coding style 
[https://docs.djangoproject.com/en/3.2/internals/contributing/writing-code/coding-style/](https://docs.djangoproject.com/en/3.2/internals/contributing/writing-code/coding-style/)
- Remove trailing whitespaces to save bytes
- Don't put your name in the code. Use AUTHORS file instead.

### 2) Underscores in URL pattern names & template block

- e.g. name='hub:curriculum_list'
- Dashes in URL is fine. e.g. 'notice-board'
- e.g. template block content_block inside two curly brackets 

## 7. JS, HTML, and CSS Style Guides

### 1) JavaScript Style Guides
unofficial but industry standard

- [github.com/standard/standard](github.com/standard/standard)
- [github.com/rwaldron/idiomatic.js](github.com/rwaldron/idiomatic.js)
- [github.com/airbnb/javascript](github.com/airbnb/javascript)
- useful tool: ESLint [eslint.org](eslint.org)

### 2) HTML and CSS Style Guides
- [https://codeguide.co/](https://codeguide.co/)

## 8. IDE (Integrated Development Environment)
Don't be too much dependent on features in IDE. Make things easier for 
everyone to navigate in the project. <br>
Always assume other developers have their own choice of tools.
e.g. template tags name: [app_name]_tags.py