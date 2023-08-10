---
title:
description: A list of outstanding Salesforce issues which bug me
pubDate: Aug 10 2023
---

1. `vscode salesforce extension`  If you start up vscode in a project it will present you a list of
   orgs to connect to in the lower left of the status bar.   The list only shows sandboxes you're
   connected to not scratch orgs.  If you want to conect to a scratch org you need to explictely set
   the scratch org as the default org within the project by running ...
   ```
   sfdx config:set defaultusername=my-scratch-org-alias
   ```

   I think Salesforce needs to do work to filter out scratch orgs from this list. Why is this
   important?   Well you might want to connect to a sandbox or production to run a query then switch
   back to your project.   Or you might be using two scratch org at the same time.   Say you're
   doing development in one and install testing in the other so you need to switch back and forth.

   This has been going on for years and the only progress has been that I have to update
   all my scripts and aliias.  The updated `sf` equivilent is...
   ```
   sf config set target-org=myscratch-org-alias
   ```




