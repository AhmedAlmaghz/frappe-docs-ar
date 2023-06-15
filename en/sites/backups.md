## Backups

Frappe Cloud takes automated backup of your sites every 6 hours.

## Downloading backups

On the site page, go to the **Backups** tab. Here you will see the list of backups that were taken of your site. Every backup consists of a database backup, public files backup and private files backup.

[![Offsite Backups](https://frappecloud.com/assets/press/images/docs/site-backups.png)](https://frappecloud.com/assets/press/images/docs/site-backups.png)

## Trigger on-demand backup

You can also trigger a manual backup operation for your site anytime from the **Backups** tab by clicking on the **Schedule Backup with Files** button.

The job will be queued and it will take a few minutes to complete.

## Offsite Backups

> Offsite backups are available for sites on USD 25 and above plans.

1 out of every 4 automated backup is stored offsite, which means the files are stored on a different server than the site. This ensures that you can access your backups even in the unfortunate event of server downtime.

Offsite backups are marked as such in the Backups tab.

### Offsite Backup Rotation

For each site, a certain number of offsite backups are kept at all times. The frequency of backups is as shown below:

*   7 daily
*   4 weekly
*   12 monthly
*   10 yearly

This is done to store backups efficiently. For example, if the current day is Jan 13, then the backups available will be like so:

[![Backups Example - December](https://frappecloud.com/assets/press/images/docs/brs-december.png)](https://frappecloud.com/assets/press/images/docs/brs-december.png)

[![Backups Example - January](https://frappecloud.com/assets/press/images/docs/brs-january.png)](https://frappecloud.com/assets/press/images/docs/brs-january.png)

(Monthly and yearly backups before December 2020 not shown in picture)

*   Weekly backups are taken every Sunday
*   Monthly backups taken every 1st day of the month
*   Yearly backups taken every 1st day of the year

## FAQ

### Why is my backup size so much smaller than database usage I see in dashboard?

This is because we store backups in compressed form as it is static and no operations are being done on it. We use standard unix tool called gzip for compressing the backups. The difference is in size is thanks to the same.

You can download the backup and decompress it with gzip to compare the size for yourself. It should be almost same as the size you see in your dashboard.