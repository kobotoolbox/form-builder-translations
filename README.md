# KPI UI Translations 

This repository contains the localisations for the [KoboToolbox KPI](https://github.com/kobotoolbox/kpi) project. 

## Update translations from Transifex

If there are new translations in Transifex that need to be pulled into the repository, run 

	tx pull --all

to pull them and then commit and push the updates to this repository. 

## Extract new ES6/Coffee translatable strings using Poedit

To update the KPI UI's translatable sources using Poedit, follow these instructions: 

* Update your Poedit preferences to include ES6 files in the Javascript Extractor (append `;*.es6` to the "List of extensions..." field).
* Update the PHP extractor, and add `*.coffee` to it. `gettext` by default doesn't have a CoffeeScript parser, but the PHP extractor works fairly well with .coffee files. 
* Open the `en/LC_MESSAGES/djangojs.po` file and run "Update from Sources". You should see a summary of the new and obsolete strings. Review and save the changes if all looks ok. 
* If you encounter `gettext` parsing error messages (you can see each error's line number in the details), check each error, and if there is a string in that line number that is missing from the sources, you can copy the missed string into `jsapp/i18nMissingStrings.es6` and rerun "Update from Sources".

## Push new source strings to Transifex

If there are new strings to translate, follow these steps to push them to Transifex: 

* From the KPI root directory, run `python manage.py makemessages --locale en`.
* Update the translatable strings as detailed in the section above.
* Run `tx push -s` to push all of the updates to Transifex.
