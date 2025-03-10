---
summary: Manage end-user roles and access in OutSystems 11 (O11) using the Users app by visiting your specific environment URL.
tags: support-Mobile_Apps; support-webapps
locale: en-us
guid: 2cbb2e7d-9936-4bb4-8791-240ade1d1ad6
app_type: traditional web apps, mobile apps, reactive web apps
platform-version: o11
figma: https://www.figma.com/file/iBD5yo23NiW53L1zdPqGGM/Developing-an-Application?type=design&node-id=280%3A44&mode=design&t=vStGeN187wwjAjiU-1
---

# Access the Users app

The OutSystems **Users** app lets you create, update, and delete [End Users](./add-delete-users.md) (the users of your apps) and their roles. You can also manage [User Roles](../user-roles/intro.md) individually or in bulk using groups.

## Navigate to the Users app

To access the Users app for a specific OutSystems environment, go to:

`https://<environment_address>/Users`

For example, if your environment address is `example.outsystemscloud.com`, go to:

`https://example.outsystemscloud.com/Users/`

## Initial configuration

Before accessing the Users app for the first time, you must configure the Administrator user. Learn how to [configure the Administrator user of the Users app](configure-admin.md).

<div class="info" markdown="1">

The Users admin account is **not** the same one you use to connect to Service Center, LifeTime or Service Studio, as those are [IT Administrator Users](../../manage-platform-app-lifecycle/manage-it-teams/intro.md).

</div>

![Screenshot of the Users app first login screen prompting for Administrator configuration](images/users-app-first-login-usr.png "Users App First Login Screen")
