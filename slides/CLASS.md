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
* help <subcommand>
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
* 

---

# Sessions & Cookies

* When do I use which?

---

## Sessions

* Track information between web requests
* Can be stored multiple ways. RAM, Database, Disk, Cookies
* Not visible to the user

---

## Cookies

* Information stored in the users browser
* Visible to the user

---

# Middleware

* Perform actions at different stages of request/response
* Independant of which view is used

Built in:

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

# Middleware Stages

Request::
  Before matching URL patterns
View::
  After matching URL pattern, before calling view
Exception::
  If the view results in an exception
Template Response::
  If the view returns a TemplateResponse
Response::
  All responses

## Order is important!

* Request / View called in order declared
* Others called in _reverse_ order

---

# Logging

---

## Django Logging Configuration

* 

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
