# Overview
This repo was created in response to [this question](https://salesforce.stackexchange.com/questions/189305/metadata-for-user-interface-options) on StackExchange:
> We wish to create a scratch org that has the `Enable "Set Audit Fields upon Record Creation" and "Update Records with Inactive Owners" User Permissions` setting checked.

Is there a scratch org definition file option available to do this that I'm not seeing. Or failing that is there a programmatic way of setting the setting? 
# Instructions
These instructions handle two steps:
1. Setting the User Interface setting of `Enable "Set Audit Fields upon Record Creation" and "Update Records with Inactive Owners" User Permissions`
2. Assigning a permission set that adds this setting to the default user

## From an existing repo and scratch org
1. In the source org
   - Run `sfdx force:source:retrieve -m Settings:Security`
   - Search the retrieved file for `enableAuditFieldsInactiveOwner` and set the value to `true`. Save the file.
2. In a new scratch org
   - Run `sfdx force:source:deploy -m Settings:Security` **immediately** after creating the scratch org
   - Run `sfdx force:source:push` as usual
   - If needed, assign any needed permission sets using `sfdx force:user:permset:assign --permsetname [yourauditfieldpermset]`

## Contents of this repo (samples)
- Simple security settings file with the audit fields setting enabled
- Permission set that allows "set audit fields upon creation"
