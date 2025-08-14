---
title:  "[Next.js] 1. Project Overview"
excerpt: ""
share: false
categories:
  - Next.js
tags:
  - [Blog, Next.js]

toc: true
toc_sticky: true
published: true
 
date: 2025-08-14
last_modified_at: 2025-08-14
---
## 1. Project
- variable names should be clear: no abbreviation
- Document classes and methods
- Repeated code into reusable ones
- Keep functions and methods short (script itself)

## 4. Explicit Relative Imports
Benefits: easier to move, rename, and version control
> "a powerful tool for separating individual modules from being tightly coupled to the architecture around them"

- Absolute import: when importing from outside the current app
- Explicit Relative: importing from another module in current app


```
# Relative imports of the 'cones' package
from .models import WaffleCone
from .forms import WaffleConeForm

```

### 1) Django coding style 
[https://docs.djangoproject.com/en/3.2/internals/contributing/writing-code/coding-style/](https://docs.djangoproject.com/en/3.2/internals/contributing/writing-code/coding-style/)
- Remove trailing whitespaces to save bytes
- Don't put your name in the code. Use AUTHORS file instead.
