## Custom Apps

### Why does it show "Attention Required" next to my custom app?

![Attention Required badge](https://frappecloud.com/files/Screenshot%202022-08-16%20at%2012.36.46%20PM.png)

This means that we are **not able to fetch the latest updates from the associated GitHub repository** for the app. This happens most probably because the Frappe Cloud GitHub app does not have the permission to access the repository. Please make sure Frappe Cloud app has proper permissions from GitHub settings. You can then retry fetching the latest update:

![Fetch Latest Updates in dropdown](https://frappecloud.com/files/fetch_updates.png)

### Workaround: Attention required even after trying the above

If you're getting the error even after adding and removing the app on Frappe Cloud, please visit [https://github.com/settings/installations/](https://github.com/settings/installations/) and then click the configure button next to the **Frappe Cloud** Github App.

![Configure Frappe Cloud Github](https://frappecloud.com/files/Screenshot%202023-04-04%20at%2023-03-52%20Build%20software%20better%20together.png)

It should take you to another page with a URL like `https://github.com/settings/installations/<unique_number>`. Copy this number (or the URL as a whole)

Now, you can raise a support ticket stating the problem (or linking this doc page) with the number you copied so that we can quickly resolve the issue from our end.