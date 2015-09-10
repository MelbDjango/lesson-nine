## MelbDjango School

### Lesson Nine — Advanced Django Topics

---

## WIFI

Common Code / cc&20!4@

---

# Management Commands

---

## Familiar Management Commands

By now, we should be familiar with the following:

* help
* help {subcommand}
* runserver
* test
* makemigrations
* migrate
* startproject (usually called from django-admin)
* startapp
* shell
* collectstatic

---

## Other Useful Commands

* createsuperuser
  * Generate an additional superuser (good when picking up badly documented projects)
* changepassword
  * Change any existing user's password
* dumpdata
  * Generate a json, xml, yaml fixture of some or all data in the database
* loaddata
  * Load fixture data into the database
* dbshell
  * Drops you to a shell for the database defined in the settings
* flush
  * Resets the database (good for dev, BAD for production)

---

##  Useful Commands Continued

* showmigrations
  * Shows the migrated state for one or all apps (equivalent to migrate --list)
* squashmigrations
  * Consolidates an app's many migrations into a single one
* sqlmigrate
  * Shows the SQL for a single migration
* sqlflush
  * Shows the SQL that if run will reset the database to the initial installation state (what "flush" runs)

---

## Writing your own management commands

* Automate regular housekeeping tasks

---

# Sessions & Cookies

* Store state in a stateless world

---

# Sessions

* Track information between web requests
* Can be stored multiple ways. RAM, Database, Disk, Cookies
* Not visible to the user

---

# Cookies

* Information stored in the users browser
* Visible to the user

---

# Cookies vs. Sessions

* Cookies are quick - no DB hit
* Sessions are secure - not visible to User

---

# Middleware

* Perform actions at different stages of request/response
* Independant of which view is used

---

# Middleware Stages

<dl>
  <dt> Request </dt>
  <dd> Before matching URL patterns </dd>
  <dt> View </dt>
  <dd> After matching URL pattern, before calling view </dd>
  <dt> Exception </dt>
  <dd> If the view results in an exception </dd>
  <dt> Template Response (i.e. CBV)</dt>
  <dd> If the view returns a TemplateResponse </dd>
  <dt> Response </dt>
  <dd> All responses </dd>
</dl>

---

## Order is important!

* Request / View called in order declared
* Others called in _reverse_ order

---

# Middleware - Built in

* Site-wide caching
* "Common"
  * Restrict user agents
  * Append slash / prepend WWW
  * E-Tags
* Broken Links Email
* GZip
* Conditional GET
* Locale
* Messages
* Security
* Session
* Site
* Authentication
* CSRF Protection
* X-Frame Options (click-jacking protection)

---

# Logging

* Keep track of what's going on inside
* Selectable "levels" to tune verbosity
* Tremendously configurable
  * Which means more complicated
* Easy to use!

```
import logging
log = logging.getLogger(__name__)

...

log.debug('We got here!')

```

---

# Logging components

* Filters
* Loggers
* Handlers
* Formatters

---

# Logging Levels

| Level    | Numeric value
|----------|--------------
| CRITICAL | 50
| ERROR    | 40
| WARNING  | 30
| INFO     | 20
| DEBUG    | 10
| NOTSET   | 0

---

# Logging: Filters

* Used in both Loggers and Handlers
* Selectively discard some messages
  * e.g. Django has django.utils.log.RequireDebugFalse

---

# Logging: Formatters

* Control how logged messages are formatted

---

# Logging: Loggers

* Where messages come into the logging pipeline
* Names act as "prefix"
* Have a "level"
  * Acts as a "squelch", or minimum
* Can have filters
* Specify a list of Handlers

---

# Logging: Handlers

* Determine where logged messages go [file, syslog, email]
* Can have a "level"
* Can have filters
* Can have a formatter

---

## Django Logging Configuration

* LOGGING setting

```
{
    'version': 1,
    'disable_existing_loggers': False,
    'formatters': {
        'standard': {
            'format': "[%(asctime)s] %(levelname)s [%(name)s:%(lineno)s] %(message)s",
            'datefmt': "%d/%b/%Y %H:%M:%S"
        },
    },
    'filters': {
        'require_debug_false': {
            '()': 'django.utils.log.RequireDebugFalse',
        },
    },
    'handlers': {
        'null': {
            'level': 'DEBUG',
            'class': 'logging.NullHandler',
        },
        'mail_admins': {
            'level': 'ERROR',
            'class': 'django.utils.log.AdminEmailHandler',
            'filters': ['require_debug_false'],
        },
        'console': {
            'level': 'DEBUG',
            'class': 'logging.StreamHandler',
            'formatter': 'standard',
        },
    },
    'loggers': {
        'django.request': {
            'handlers': ['mail_admins'],
            'level': 'ERROR',
            'propagate': True,
        },
        'accounts': {
            'handlers': ['console'],
            'level': 'INFO',
        },
        'utils': {
            'handlers': ['console'],
            'level': 'DEBUG',
        },
    }
}
```


---

# Cache

---

## Cache Uses

* Provide a faster delivery mechanism for commonly accessed information
*

---

## Cache storage

* Like sessions can be stored in RAM, Database, Disk
* 

---

# Signalling

---

## Model Signals

pre_init, post_init, pre_save, post_save, pre_delete, post_delete, m2m_changed, class_prepared

## Management signals

pre_migrate, pre_syncdb, post_migrate, post_syncdb

---

## Request/Response Signals

request_started, request_finished, got_request_exception

## Test signals

setting_changed, template_rendered

## Database Wrappers

connection_created

---

## Signal handlers

---

# Custom template tags

---

# Present your project at MelbDjango
