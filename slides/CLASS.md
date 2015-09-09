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

---

## Sessions

* Track information between web requests
* Can be stored multiple ways. RAM, Database, Disk
* 

---

## Cookies

* Used by the web server to reference session specific information
* 

---

# Middleware

---

## Custom Middleware

* Perform custom actions with every request
* 

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