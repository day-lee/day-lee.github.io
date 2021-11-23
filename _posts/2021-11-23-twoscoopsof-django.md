---
title:  "[Two Scoops of Django 3.x] 1. Coding Style"
excerpt: ""

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
# 1. Readable code matters!
- variable names should be clear: no abbreviation
- Document classes and methods
- Repeated code into reusable ones
- Keep functions and methods short

# 2. PEP 8
official guide of Python
- 4 spaces for indentation
- 2 blank lines btw top-level function and class definitions
- 1 blank line btw method definitions inside a class 
  (Black: code formatter, Flake8: checking code quality)
- 79-character limit

# 3. Imports
Imports should be grouped as follows:
- Standard library imports (from os.path import abspath)
- Core Django imports  (from django.db import models)
- Related third-party 
- From your Local app (from app.models import ExampleModel)

# 4. Explicit Relative Imports
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

# 5. Avoid Using Import * 
Python Naming Collisions 

# 6. Django Coding Style
6.1 Consider the Django Coding Style
6.2 Use Underscores in URL Pattern Names Rather Than Dashes 
6.3 Use Underscores in Template Block Names Rather Than Dashes

# 7. JS, HTML, and CSS Style Guides
7.1 JavaScript Style Guides 
7.2 HTML and CSS Style Guides 

# 8. IDE 
