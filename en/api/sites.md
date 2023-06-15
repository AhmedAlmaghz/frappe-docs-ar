## Sites

All requests require `Authorization` and `X-Press-Team` headers.

```
import requests

headers = {
    "Authorization": "Token <api-key>:<api-secret>",
    "X-Press-Team": "<team>"
}
requests.get("https://frappecloud.com/api/method/press.api.account.me", headers=headers).json()
```

However, for the sake of brevity, the above snippet is represented as

```
requests.get("https://frappecloud.com/api/method/press.api.account.me")
```

### List all Sites

**Request**

```
requests.get("https://frappecloud.com/api/method/press.api.site.all")
```

**Response**

```
{
    "message": [
        {
            "name": "shared",
            "shared": true,
            "status": "Active",
            "sites": [
                {
                    "name": "site-1.erpnext.com",
                    "status": "Active",
                    "bench": "bench-0198-002761-f3"
                }
            ]
        },
        {
            "name": "bench-0000",
            "title": "Version 13",
            "version": "Version 13",
            "benches": [
                {
                    "name": "bench-0000-000000-f0",
                    "status": "Active"
                }
            ],
            "sites": [
                {
                    "name": "site-2.frappe.cloud",
                    "status": "Active",
                    "bench": "bench-0000-000000-f0"
                }
            ]
        }
    ]
}
```

### Get a Site

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.get", json=data)
```

**Response**

```
{
    "message": {
        "name": "site-0.frappe.cloud",
        "status": "Active",
        "frappe_version": "Version 13",
        "server_region_info": {
            "title": "Cape Town, South Africa"
        }
    }
}
```

### Get Options for Creating a Site

```
requests.get("https://frappecloud.com/api/method/press.api.site.options_for_new")
```

**Response**

```
{
    "message": {
        "plans": [
            {
                "name": "USD 10"
            },
            {
                "name": "USD 25"
            }
        ],
        "versions": [
            {
                "name": "Version 13",
                "groups": [
                    {
                        "name": "bench-0001",
                        "title": "Version 13",
                        "apps": [
                            {
                                "app": "frappe",
                                "repository_url": "https://github.com/frappe/frappe",
                                "branch": "version-13"
                            },
                            {
                                "app": "erpnext",
                                "repository_url": "https://github.com/frappe/erpnext",
                                "branch": "version-13"
                            }
                        ],
                        "clusters": [
                            {
                                "name": "Mumbai"
                            },
                            {
                                "name": "Frankfurt"
                            },
                            {
                                "name": "Bahrain"
                            },
                            {
                                "name": "Cape Town"
                            },
                            {
                                "name": "N. Virginia"
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
```

### Create a Site

**Request**

```
data = {
    "site": {
        "name": "site-0",
        "apps": [
            "frappe",
            "erpnext"
        ],
        "group": "bench-0001",
        "cluster": "Cape Town",
        "plan": "USD 10",
    }
}

requests.post("https://frappecloud.com/api/method/press.api.site.new", json=data)
```

**Response**

```
{
    "message": {
        "site": "site-0.frappe.cloud",
        "job": "0000000000"
    }
}
```

You will immediately receive a response for this request, with the site name. You could then poll site status using [Get a Site](https://frappecloud.com/docs/api/sites#get-a-site). The site could be used after the site status is `Active`.

### Drop a Site

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.archive", json=data)
```

**Response**

```
{}
```

### Deactivate a Site

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.deactivate", json=data)
```

**Response**

```
{}
```

### Activate a Site

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.activate", json=data)
```

**Response**

```
{}
```

### List all Backups

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.backups", json=data)
```

**Response**

```
{
    "message": [
        {
            "with_files": 1,
            "database_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-database.sql.gz",
            "private_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-private-files.tar",
            "public_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-files.tar",
            "creation": "0000-00-00 00:00:00.000000",
            "offsite": 1
        }
    ]
}
```

### Schedule a Backup

**Request**

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.backup", json=data)
```

**Response**

```
{}
```

### Login As Administrator

```
data = {
    "name": "site-0.frappe.cloud",
}

requests.post("https://frappecloud.com/api/method/press.api.site.login", json=data)
```

**Response**

```
{
    "message": "00000000000000000000000000000000000000000000000000000000"
}
```

You could the use the response as sid cookie to login to your site

```
cookies = {
    "sid": "00000000000000000000000000000000000000000000000000000000",
}

requests.post("https://site-0.frappe.cloud/api/method/frappe.auth.get_logged_user", cookies=cookies).json()
# {'message': 'Administrator'}
```