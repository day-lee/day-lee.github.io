---
title:  "[Two Scoops of Django 3.x] 5. Settings and Requirements Files"
excerpt: ""
share: false
categories:
  - Django 

toc: true
toc_sticky: true
published: true
 
date: 2021-11-28
last_modified_at: 2021-11-28
---


## 1. Django settings

### 1) Local Settings
  - Django has over 150 settings with default values
  - Change settings in production require a server restart

### 2) Best Practices
  - Version control for settings is a must
  - Keep SECRET_KEY safe and any other API keys, out of version control <br>
  Production database passwords, AWS keys, OAuth tokens etc
  
### 3) Problems
- local_settings.py which is location-specific settings
possibly can cause problems as it's different from production settings. <br>
such as when fixed bugs locally and pushed to production only to find crashing...because of differences in settings 

## 2. Using Multiple Settings Files 
- settings/ directory instead of settings.py
- Each settings module requires its own requirements file

```
settings/
├── __init__.py
├── base.py       -> common to all instances of the project
├── local.py      -> locally develop: DEBUG mode, log level
├── staging.py    -> managers, clients confirm before production 
├── test.py       -> test runners, in-memory database definitions, log settings 
├── production.py -> (== prod.py) live production server  

```

### Commands
```
# start python interactive interpreter with django
python manage.py shell --settings=config.settings.local

# runserver
python manage.py runserver --settings=config.settings.local

```

### 1) Development Settings Example

settings/local.py
- No need to use if DEBUG, if not DEBUG logic with this. 

```
from .base import *

DEBUG = True
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
DATABASES = {
'default': {
'ENGINE': 'django.db.backends.postgresql',
'NAME': 'twoscoops',
'HOST': 'localhost',
}
}
INSTALLED_APPS += ['debug_toolbar', ]


```

### 2) Multiple Development Settings 
- Set your own local settings.py and keep it in version control for teammates

```
base.py
local_daylee.py
local_teammate.py
```

## 3. Separate Configuration From Code
### Use Environment Variables Pattern
Benefits
- You can store settings file in version control 
- Most platforms-as-a-service has built-in feature for settings as environment variables 


### 1) A Caution Before Using Environment Variables for Secrets  
- Require good understanding of bash with environment variables 
- Willingness to host your project on a PaaS(platform-as-a-service) 
- A way to manage the secret information 

[Environment variables](en.wikipedia.org/wiki/Environment_variable
)
>  An environment variable is a dynamic-named value that can affect the way running processes 
> will behave on a computer. 
- Warning: Apache has its own environment variable system. 
Environment Variables described below won't work on Apache

### 2) How to Set Environment Variables Locally 
   

- Bash for the shell (pre-Catalina Mac and Linux distributions) can add lines
at the end of ```.bashrc, .bash_profile, or .profile. ```
Macs on Catalina and afterwards use ```.zshrc.``` 
- Multiple projects using same API but with different keys: end the of your virtualenv’s bin/postactivate script

```
export SOME_SECRET_KEY=1c3-cr3am-15-yummy
```

- on Windows
at the command line
(cmd.exe)
- reopen your command prompt for them to go into effect
- at the end of the virtualenv’s bin/postactivate.bat script, so they are available upon activation:

```
 setx SOME_SECRET_KEY 1c3-cr3am-15-yummy
```
- Powershell

```
# user-only
[Environment]::SetEnvironmentVariable('SOME_SECRET_KEY',
'1c3-cr3am-15-yummy', 'User')

# machine-wide
[Environment]::SetEnvironmentVariable('SOME_SECRET_KEY',
'1c3-cr3am-15-yummy', 'Machine')

```

### 3) How to Unset Environment Variables Locally  
- Environment variables remain set until it is unset,
  the shell is ended. <br> It remains even though you deactivated the virtualenv,

>You can set your own variables at the command line per session, or make them permanent by placing them 
> into the ~/.bashrc file, ~/.profile, or whichever startup file you use for your default shell.
> https://www.redhat.com/sysadmin/linux-environment-variables

- Most time, remaining environment variables is fine. But if you want to tightly control it

``` 
# on Linux/OSX/Windows
unset SOME_SECRET_KEY 
 
# Powershell
[Environment]::UnsetEnvironmentVariable('SOME_SECRET_KEY', 'User')
```

### 4) How to Set Environment Variables in Production 
- If using Paas such as Heroku, Python Anywhere, platform.sh etc, follow the specific instructions
- From Python side, open up a new Python prompt 

``` 
# Top of settings/production.py
import os
SOME_SECRET_KEY = os.environ['SOME_SECRET_KEY'] 
```

### 5) Handling Missing Secret Key Exceptions 
- KeyError comes up if SECRET_KEY is not available, which makes it hard to start a project itself.
- Code below allows you to have clear error message.

get_env_variable() Function

``` 
# settings/base.py
import os
# Normally you should not import ANYTHING from Django directly
# into your settings, but ImproperlyConfigured is an exception.

from django.core.exceptions import ImproperlyConfigured

def get_env_variable(var_name):
  """Get the environment variable or return exception."""
  try:
    return os.environ[var_name]
  except KeyError:
    error_msg = 'Set the {} environment variable'.format(var_name)
    raise ImproperlyConfigured(error_msg)


# in any of your settings file
SOME_SECRET_KEY = get_env_variable('SOME_SECRET_KEY')
```



- Packages <br>
[github.com/joke2k/django-environ](github.com/joke2k/django-environ) (Used in Cookiecutter Django)
[github.com/jazzband/django-configurations](github.com/jazzband/django-configurations)



## 4. When You Can’t Use Environment Variables 
- Using environment variables to store secrets doesn't always work especially for cases below:

```  
Nginx-based environment 
Apache for serving HTTP 
```

### Secrets File Pattern

#### 1) Using JSON Files 

- Placed in project directory at secrets.json
- Make sure to put it in .gitignore

```
{
"SECRET_KEY": "mthisistheverysecuredkey@h%2pq0"
}
```

- Example from my own [notice-board1.11 project](https://github.com/day-lee/notice-board1.11/blob/master/test_board/settings.py) 

```  
import os, json
from django.core.exceptions import ImproperlyConfigured

BASE_DIR = os.path.dirname(os.path.dirname(os.path.abspath(__file__)))

# SECRET KEY
secret_file = os.path.join(BASE_DIR, 'secrets.json')

with open(secret_file) as f:
    secrets = json.loads(f.read())
def get_secret(setting, secrets=secrets):
    # Get secret variable or return exception
    try:
        return secrets[setting]
    except KeyError:
        error_msg = "Set the {} environment variable".format(setting)
        raise ImproperlyConfigured(error_msg)

SECRET_KEY = get_secret("SECRET_KEY")

```

#### 2) Using .env, Config, YAML, and XML File Formats 
- Writer prefers simple JSON format, other formats are up to you

## 5. Using Multiple Requirements Files 
### 1) Installing From Multiple Requirements Files 
- Segmented Requirements

```  
 requirements/
├── base.txt       -> dependenvies used in all enviroments
├── local.txt
├── staging.txt
├── production.txt
```

- Command

``` pip install -r requirements/local.txt ```

## 6. Handling File Paths in Settings
- Never hardcode your paths, as fixed path will not work in other's computers 
- Solution: project root variable as `BASE_DIR`, use Pathlib to discover project root


 