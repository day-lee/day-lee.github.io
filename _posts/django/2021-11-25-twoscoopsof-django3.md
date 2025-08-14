---
title:  "[Two Scoops of Django 3.x] 3. Django Projects Layout (Structure) "
excerpt: ""
share: false
categories:
  - Django
tags:
  - [Blog, Django]

toc: true
toc_sticky: true
published: false
 
date: 2021-11-25
last_modified_at: 2021-11-25
---

## 1. Default project layout

- when ```django-admin startproject projectname```, <br>
default layout is created, and it's not suitable for most of the real world projects.

## 2. Recommended Project Layout 
```
<repository_root>/
├── <configuration_root>/
├── <django_project_root>/
```
### 1) Top Level: Repository Root
- Includes README.md, docs/ directory, manage.py, .gitignore, requirements.txt
- Makefile: simple deployment tasks and macros
- files for deployment
### 2) Second Level: Django Project Root 
- Django Project 
- media: for development only. User-generated static media assets. 
- static(assets): Non user-generated static media assets including CSS, JS, and images
- For larger projects, Both media and static will be hosted on separate static media servers

### 3) Second Level: Configuration Root 
- URLConf(urls.py), settings, asgi.py, wsgi.py

## 3. Sample Project Layout 

```
django_project
├── config/ 
│   ├── settings/
│   ├── __init__.py
│   ├── asgi.py
│   ├── urls.py
│   └── wsgi.py
├── docs/
├── app/
│   ├── media/ # Development only!
│   ├── products/
│   ├── profiles/
│   ├── ratings/
│   ├── static/
│   └── templates/
├── .gitignore
├── Makefile
├── README.md
├── manage.py
└── requirements.txt
```

## 4. Virtualenv
- a separate "virtualenv" directory for all of your Python projects 
```
# example path
~/projects/icecreamratings_project/
~/.envs/icecreamratings/
```
- no need to upload environment directories to public repos: Use .gitignore
- requirements.txt: pip freeze to save list of dependencies 


## 5. Project templating boilerplate tool: Cookiecutter
[https://cookiecutter.readthedocs.io/en/latest/](https://cookiecutter.readthedocs.io/en/latest/)
### How Cookiecutter works?
- enter a series of values: project names etc.
- Cookiecutter generates boilerplate project files. 
- fork Cookiecutter Django and customize it to fit your own Django
project needs.


References
- [github.com/pydanny/cookiecutter-django](github.com/pydanny/cookiecutter-django)
- [github.com/grantmcconnaughey/cookiecutter-django-vue-graphql-aws](github.com/grantmcconnaughey/cookiecutter-django-vue-graphql-aws)

- Alternative cookiecutter templates.
<br> [djangopackages.org/grids/g/cookiecutters/](djangopackages.org/grids/g/cookiecutters/)