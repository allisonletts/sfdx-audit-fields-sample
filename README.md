# Instructions
These instructions handle two steps:
1. Setting the User Interface setting of `Enable "Set Audit Fields upon Record Creation" and "Update Records with Inactive Owners" User Permissions`
2. Assigning a permission set that adds this setting to the default user

## From an existing repo and scratch org
1. In the source org
   1. Run `force:source:retrieve -m Settings:Security`
   2. Search the retrieved file for `enableAuditFieldsInactiveOwner` and set the value to `true`
2. In a new scratch org
   1. Run `force:source:deploy -m Settings:Security` **immediately** after creating the scratch org
   2. Run `force:source:push` as usual
   3. If needed, assign any needed permission sets using `sfdx force:user:permset:assign --permsetname [yourauditfieldpermset]`

## Contents of this repo (samples)
- Simple security settings file with the audit fields setting enabled
- Permission set that allows "set audit fields upon creation"