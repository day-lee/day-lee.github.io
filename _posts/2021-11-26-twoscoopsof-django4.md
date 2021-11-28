---
title:  "[Two Scoops of Django 3.x] 4. Fundamentals of Django App Design "
excerpt: ""
share: false
categories:
  - Django
tags:
  - [Blog, Django]

toc: true
toc_sticky: true
published: true
 
date: 2021-11-26
last_modified_at: 2021-11-26
---
 

## 1. Name convention for Django App 

- App should be minimal as possible, should be explained in one sentence!
- Name convention: single word names clearly describe the app feature
- App name should be a plural version of main model  
- Consider name corresponds with urls (visible to the public) to navigate easily
- According to PEP 8: Python package name should be short, all-lowercase, w/o
numbers, dashes, periods, spaces, or special characters. Use of underscores is discouraged.

## 2. Keep Apps small
> Don’t worry too hard about getting app design perfect. It’s an art, not a science. Sometimes
you have to rewrite them or break them up. That’s okay.

## 3. App Modules
### 1) Common App Modules 
```
# Common modules
scoops/
├── __init__.py
├── admin.py
├── forms.py
├── management/
├── migrations/
├── models.py
├── templatetags/
├── tests/
├── urls.py
├── views.py

```


### 2) Uncommon App Modules 
For further explanation refer to 4.4.2 Uncommon App Modules (p.74)
Uncommon App modules are used as the project gets bigger and needs some kind of separation for clarity

```
# uncommon modules
scoops/
├── api/
├── behaviors.py
├── constants.py
├── context_processors.py
├── decorators.py
├── db/
├── exceptions.py
├── fields.py
├── factories.py
├── helpers.py
├── managers.py
├── middleware.py
├── schema.py
├── signals.py
├── utils.py
├── viewmixins.py
```

## 4. App design

### Alternative: Ruby on Rails-Style Approaches
- Django and Rails are similar as it is for Python and Ruby
- Rails projects are GitHub, GitLab, Coinbase, Stripe, and
Square.

#### 1) Service Layers 
- How to organise the business logic
- OOP
- Loose coupling, so any changes can be readily replaced
```
seperating code in different files
services.py, selectors.py 
```

#### 2) The Large Single App Project 
- Django is heavily based on convention over configuration(customising)

e.g. models/users.py , models/tickets.py