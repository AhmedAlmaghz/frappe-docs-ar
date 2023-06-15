## Database Access

> Database Access is available for sites on USD 50 and above plans

You will now have complete access to your site's database.

### Enable Database Access

Go to Site Dashboard > Database > Access.

![Enable Database Access](https://frappecloud.com/files/database-access-enable.png)

Click Enable Access if you haven't previously used this feature. Now you'll see credentials to connect your database.

![Database Access Credentials](https://frappecloud.com/files/database-access-credentials.png)

### Connect to the Database

#### Analytics or Business Intelligence tool

Copy the credentials shown to your analytics tool.

We only allow TLS connections. If you're having issues while connecting then please ensure that the analytics tool is using SSL/TLS and our certificate [chain.pem](https://frappecloud.com/files/chain.pem) for `*.frappe.cloud` (Signed by [Let's Encrypt](https://letsencrypt.org/)).

#### MariaDB/MySQL command line client

![Database Access CLI](https://frappecloud.com/files/database-access-cli.png)

Copy the command to your console and paste the password when prompted.

You will need to install [mariadb-client or mysql-client](https://mariadb.com/docs/server/connect/clients/mariadb-client/) on your machine.

> You now have **read-write** access to your database. Any changes made to your database will be permanent.

### FAQ: Cannot connect to database from PowerBI

If connecting with PowerBI doesn't work, you might be using MySQL Connector. We use MariaDB for our databases. Please use Mariadb connector with PowerBI for the same. You can find docs for the same [here](https://mariadb.com/resources/blog/getting-started-with-the-mariadb-direct-query-adapter-for-microsoft-power-bi/).