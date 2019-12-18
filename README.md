# KPI UI Translations 

This repository contains the localisations for the [KoboToolBox KPI](https://github.com/kobotoolbox/kpi) project.

You might be wondering: "I just added a new string to KPI. How do I translate it?" You're in the right place!

## Step 1: Extract new ES6/Coffee translatable strings using Poedit

To update the KPI UI's translatable sources using Poedit, follow these instructions: 

* :warning: Do not use version 2 of Poedit! These steps have been tested to work on version 1.8.
* Clone [KPI](https://github.com/kobotoolbox/kpi) if you have not done so already.
* From the KPI root directory, run `git submodule update --init --remote --recursive` to retrieve the latest files from this `form-builder-translations` repository.
* Open Poedit. The first time you run it, you'll need to configure it to parse ES6 and CoffeeScript files:
    * Enable ES6 parsing:
        1. Click File, Preferences, and choose the Extractors tab.
        1. Click JavaScript and click the Edit button.
        1. Append `;*.es6` to the "List of extensions…" field.
        1. Click OK and close the Preferences window but leave the Preferences window open.
    * Enable CoffeeScript parsing. By default, `gettext` doesn't have a CoffeeScript parser, but the `C/C++` extractor works fairly well with .coffee files.
        1. Inside the Extractors tab of the Preferences window, click PHP.
        1. Click the Edit button.
        1. Append `;*.coffee` to the "List of extensions…" field.
        1. Click OK and close the Preferences window.

    **N.B.: C/C++ requires all string to be wrapped in double-quotes.**

    - `_t('Foo')` won't be detected
    - `_t("Foo")` will be detected

* Still within Poedit, open the `locale/en/LC_MESSAGES/djangojs.po` (inside the KPI root directory) file with Poedit. We are opening the English file because we're just extracting strings: the actual translation takes place on Transifex.
    * Ignore the "Language of the translation is the same as source language" warning.
* Click the Catalog menu and click "Update from Sources". You should see a summary of the new and obsolete strings. Review and save the changes if all looks ok.
* If you encounter `gettext` parsing error messages (you can see each error's line number in the details), check each error, and if there is a string in that line number that is missing from the sources, you can copy the missed string into `jsapp/i18nMissingStrings.es6` and rerun "Update from Sources".

## Step 2: Extract translatable strings from Python files

* From the KPI root directory, run `python manage.py makemessages --locale en`.
* Verify that new strings appear in `locale/en/LC_MESSAGES/django.po` (inside the KPI root directory).

## Step 3: Upload the new strings to Transifex

* Install the Transifex client if you haven't already (`pip install transifex-client`).
* From the `locale` directory inside the KPI root, run `tx push -s` to push all of the updates to Transifex.

## Step 4: Use the Transifex web interface to translate the new strings

* The Transifex project is called "koboform" and is available at https://www.transifex.com/kobotoolbox/kobotoolbox/.

## Step 5: Retrieve the new translations from Transifex and commit to this repository

* From the `locale` directory inside the KPI root, run `tx pull --all`;
* Commit and push the updates to this repository, `form-builder-translations`, whose root should be the `locale` directory.
