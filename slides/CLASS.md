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

## Rewinding Database Migrations

Check auth app migrations state

```
$ python manage.py showmigrations auth
auth
 [X] 0001_initial
 [X] 0002_alter_permission_name_max_length
 [X] 0003_alter_user_email_max_length
 [X] 0004_alter_user_username_opts
 [X] 0005_alter_user_last_login_null
 [X] 0006_require_contenttypes_0002
```

How to undo last 2 migrations in auth app?

---

## Rewinding Database Migrations

Take auth app to migration 0004

```
$ python manage.py migrate auth 0004
Operations to perform:
  Target specific migration: 0004_alter_user_username_opts, from auth
Running migrations:
  Rendering model states... DONE
  Unapplying auth.0006_require_contenttypes_0002... OK
  Unapplying auth.0005_alter_user_last_login_null... OK
```

App migration state after operation

```
$ python manage.py showmigrations auth
auth
 [X] 0001_initial
 [X] 0002_alter_permission_name_max_length
 [X] 0003_alter_user_email_max_length
 [X] 0004_alter_user_username_opts
 [ ] 0005_alter_user_last_login_null
 [ ] 0006_require_contenttypes_0002
```
