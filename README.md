# KPI UI Translations 

This repository contains the localisations for the [KoboToolBox KPI](https://github.com/kobotoolbox/kpi) project.

You might be wondering: "I just added a new string to KPI. How do I translate it?" You're in the right place!

## Step 1: Convert Frontend Strings JSON to PO file

⚠️ This process does not work unless you are using a Linux environment

* Install the translate toolkit
   ```
   sudo apt install translate-toolkit
   ```
* Once installed, move to the KPI root director and run the following command
   ```
   json2po jsapp/compiled/extracted-stings.json locale/en/LC_MESSAGES/djangojs.po
   ```
* Save copy the metadata from the old strings to the new ones

## Step 2: Extract translatable strings from Python files

* From the KPI root directory, run `python manage.py makemessages --locale en`.
* Verify that new strings appear in `locale/en/LC_MESSAGES/django.po` (inside the KPI root directory).

## Step 3: Upload the new strings to Transifex

* Install the Transifex client if you haven't already (`pip install transifex-client`).
* From the `locale` directory inside the KPI root, run `tx push -s` to push all of the updates to Transifex.

## Step 4: Use the Transifex web interface to translate the new strings

* The Transifex project is called "kobotoolbox" and is available at https://www.transifex.com/kobotoolbox/kobotoolbox/.

## Step 5: Retrieve the new translations from Transifex and commit to this repository

* From the `locale` directory inside the KPI root, run `tx pull --all`;
* Commit and push the updates to this repository, `form-builder-translations`, whose root should be the `locale` directory.
