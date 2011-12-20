This module manages the CiviCRM translations using the Drupal locale module.

It is an experiment to see if it can be more efficient (performance) and make
it easier for site administrators to translate strings from CiviCRM extensions
or custom Smarty templates.

Download: https://github.com/mlutfy/civicrm_l10n

KNOWN ISSUES:
-------------

- Drupal complains that 8 strings have illegal HTML (on aprox. 10 230 strings).
- Plural forms might not be managed correctly (not tested).

INSTALL:
--------

In short, you need to enable the module and import the translation files.
There are a few ways to get the translations for your language:

1- Less technical, but slower: Download each file from 
   https://github.com/civicrm/l10n/tree/master/po

2- More technical, but faster: use gettext to un-format the files
   shipped with the civicrm-l10n.tar.gz archive:

- install the "gettext" utilities (Debian/Ubuntu: sudo apt-get install gettext)
- un-format the civicrm.mo file: msgunfmt civicrm.mo > civicrm.po

3- Bleeding edge translations:

- create an account on Transifex (www.transifex.net)
- download the latest files from there, or use the command line client
- for more information: 

  http://wiki.civicrm.org/confluence/display/CRMDOC41/Transifex+howto
  http://wiki.civicrm.org/confluence/display/CRMDOC41/CiviCRM+Localisation
  http://wiki.civicrm.org/confluence/display/CRMDOC41/Internationalization+and+localization

Now that you have the translation files in ".po" format:

* Enable the module (drush en civicrm_l10n)
* Go to admin/config/regional/translate/import and import the files.

Note that this modules uses the hook_civicrm_config() to override the
"custom translation function" variable. There is no need to configure
it manually.


UN-INSTALL:
-----------

* Disabling the module will make CiviCRM use its own translation function
  automatically. There is no further configuration necessary (since this
  module uses hook_civicrm_config).

* Un-installing will attempt to clean out the locales_source and locales_target
  database tables by removing all strings with a "location" in "CRM/%".

