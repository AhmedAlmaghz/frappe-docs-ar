## Site

### My site is in **Inactive** state, why is it getting billed?

Both "Active" and "Inactive" sites are billed, you have to drop the site in order to suspend billing.

### My site is suspended, what do I do?

You can pay your pending invoices to unsuspend your site. You can do the same from the billing section in your FC dashboard

### What is using up all my database size?

You can see which tables/doctypes are using most space within your site itself. Search for **Database storage report** in the search bar and you will find report like follows ![Database Storage report](https://user-images.githubusercontent.com/9079960/196618374-5b268f58-b213-458f-8390-8b8beb404cdf.png)

#### Clearing logs

More often than not, log tables can take up a lot of space. You can control size of log tables with: [Log Settings](https://docs.erpnext.com/log-settings)

### What is the difference between Database and Disk space?

When you create data in your site, for e.g., Sales Invoices it will consume database space. When you upload files and images, it will consume disk space.

> You might find database space used on dashboard is higher than your actual database size when you download it on your machine. This is because on Frappecloud it is sum of space consumed by each table and index of each table. Click here to know more about [database indexes](https://www.codecademy.com/article/sql-indexes).

| Space | Files |
| --- | --- |
| Database | Database + Indexes |
| Disk | Public + Private Files |

### What's causing request timeout error?

If a particular action in your site (not all), say submission of a document takes too long and eventually ends with a Request timeout, it's an application issue assuming normal functioning of the server. In most cases we can't do much other than try increasing the default timeout of 2 minutes of web requests.

If the action you're performing is part of your custom app, we'd suggest you look into try and optimizing the code so that it finishes faster. If you're pressed for time, you may also run the particular action from `bench console` after [ssh](https://frappecloud.com/docs/benches/ssh) as a workaround.

If the action is guaranteed to take long, consider converting the same to a [background job](https://frappeframework.com/docs/v14/user/en/guides/app-development/running-background-jobs).

On the off chance that the app is not part of custom app and all other activities in the site are going smoothly, please reach out to [ERPNext Support](https://hisabcloud.com/pricing) for help.