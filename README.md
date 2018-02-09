# KPI UI Translations 

## Translation using Poedit

To translate the KPI UI using Poedit, follow these instructions: 

* update your Poedit preferences to include ES6 files in the Javascript Extractor (append `;*.es6` to the "List of extensions..." field)
* update the PHP extractor, and add `*.coffee` to it. `gettext` by default doesn't have a CoffeeScript parser, but the PHP extractor works fairly well with .coffee files. 
* open the `en/LC_MESSAGES/djangojs.po` file and run "Update from Sources". You should see a summary of the new and obsolete strings along with some `gettext` parsing error messages. Review the messages, and save the changes if all looks ok. 
* if there are errors with line numbers, check those line numbers, and if appropriate, copy the missed string into `jsapp/i18nMissingStrings.es6`.