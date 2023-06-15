## Migrate an existing site

Restore an existing site by uploading backup files or by using bench from your local setup or from your cloud provider.

> While migrating existing sites using the Frappe Cloud dashboard, some users miss the step to restore the site config details. If you're using the bench command, you won't have to worry about this.

## Restore from Backup Files

The easiest way to migrate an existing site on Frappe Cloud is to restore it from backup files.

1.  [Download backup](https://docs.erpnext.com/docs/user/manual/en/setting-up/data/download-backup) files of your site.
2.  You must have 3 files that should be named like the following:
    *   20210817\_125915-sitename-database.sql.gz (Database)
    *   20210817\_125915-sitename-files.tar (Public Files)
    *   20210817\_125915-sitename-private-files.tar (Private Files)
3.  Click on **New Site** from the Sites tab in the Frappe Cloud Dashboard.
4.  Fill out the subdomain and select the version.
5.  Click on **Create Site from Backup**.
6.  Now, upload each file you got in Step 2 in their corresponding upload boxes.
7.  Select a Plan.
8.  Click on **Create Site**.
9.  When the site reaches Active state, you will now have to restore your [site config's details](https://frappecloud.com/docs/sites/site-config).

> This method is ideal if your backup file's size is less 200MB. If you have larger backup files, you should use the `bench` command to migrate your site.

### Encryption Key

This key is used to encrypt passwords. This key is created automatically on a fresh site. Upon restoring a site from backup, this key will have to be copied into the site config as well to be able to use existing passwords.

In cases where you have lost your previous encryption key, and system has already generated a new key for you (you can verify this in your Frappe Cloud dashboard), you may stumble upon an "Encryption Key error". This is because certain password fields were encrypted using the old key. Now when then system tries to use those passwords, it fails as it tries to decrypt those passwords with the new key. In such cases, re-entering the value in those password fields will fix the problem (same password as before is fine). This works as re-entering the password will again encrypt the password using the new key.

Eg: **Email Account** is a common doctype who's document has a password field. You will want to re-enter the annotated password field if you face errors while sending email.

![](https://frappecloud.com/files/email-account-password163dd0.png)

## Migrate using site URL

While creating a new site using the new site creation wizard, you can go the **Migrate from Site URL** tab while in the **Restore from Existing Site** step and follow the given steps:

![Migrate from Site URL](https://frappecloud.com/files/migrate_from_site_url.png)

*   Enter your existing site url
*   Enter your old site user credentials
*   And click on Get Backups

Get Backups will fetch backup files from your old site to restore on Frappe Cloud.

## Migrate using Bench

If you are running Frappe sites, most likely you have `bench` installed. You can run the following command to restore a site from your bench to Frappe Cloud.

```
bench --site {name} migrate-to frappecloud.com
```

You can run this command even from your local setup. If your site is hosted on a cloud provider like Digital Ocean or Amazon AWS, you must SSH into your server, and run this command.

The bench command provides a form similar to the dashboard UI. It's probably the easiest way to migrate your site to Frappe Cloud.

![bench migrate-to command](https://frappecloud.com/assets/press/images/docs/bench-migrate-to.png)

> This method will work only if your sites are on Version 11 or greater. If you are on an older version or this command didn't work for you, you can try the Python Script method explained later.

## Migrate using Python Script

If you are on an older version of Frappe (older than version 11) or the Bench command didn't work for you, you can try this method.

Make sure you have `wget` installed. Run the following commands from your bench directory:

```
wget https://frappecloud.com/assets/press/migrate
chmod +x migrate
./migrate
```