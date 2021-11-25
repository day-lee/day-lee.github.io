---
title:  "[Two Scoops of Django 3.x] 2. Django Environment Setup"
excerpt: ""

categories:
  - Django
tags:
  - [Blog, Django]

toc: true
toc_sticky: true
published: true
 
date: 2021-11-24
last_modified_at: 2021-11-24
---

## 1. Use the same database for development and production 
- Even though you can generate SQL dump and import it to local DB, it's not an exact copy
- Different database (SQLite3, MySQL etc) handle type casting differently 
- SQLite3 has dynamic, weak typing. MySQL, PostgreSQL are strongly typed.
- Different DBs have different field types, constraints
- Sometimes, Django ORM cannot catch forms and model validation mistakes
- PostgreSQL is recommended for Django project
- Fixtures are simple, fake datasets for testing during initial setting up, 
but not reliable for migrating large data sets 
 [https://docs.djangoproject.com/en/3.2/howto/initial-data/](https://docs.djangoproject.com/en/3.2/howto/initial-data/)

## 2. Pip and Virtualenv or venv
- Pip: Python Package Index 
- Virtualenv: isolated python environments for managing package dependencies 

- Alternatives: Conda, Poetry, Pipenv
- virtualenvwrapper: to activate Virtualenv easily

```markdown
# without virtualenvwrapper (to activate the virtualenv)
source ~/.virtualenvs/twoscoops/bin/activate

# with virtualenvwrapper
workon project
```

## 3. Pip install Django and other dependencies  
- requirements file to keep the list of dependencies 

## 4. Git For Version Control 
Keep track of code changes
- hosting repositories: GitHub, GitLab

## 5. Docker for identical environments 
### Benefits
- No OS difference, No Python setup diffs, No developer-to-developer diffs 
, Closely matching environment for development and production servers.

- (Setting up Python properly is hard...)
- Docker containers share the host OS but have own isolated process and memory space.
- can be built quickly off of a snapshot 

### Downsides
- Too complicated for simple projects that's no need to worry about OS-level differences
- Even lightweight containers can slow down old machines performance

