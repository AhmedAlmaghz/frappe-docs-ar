## Custom Domains

## Adding a custom domain

Frappe Cloud allows you to map custom domains that you own in a few simple steps.

1.  Create DNS records from the dashboard of your domain provider. Follow one of the steps below:
    
    **Subdomain**: To point a subdomain to your site, add a CNAME record pointing your subdomain to your site. For example, if you want to use `www.example.com` for your site `example.frappe.cloud` then add CNAME record for `www.example.com` pointing to `example.frappe.cloud`. For the instructions to add such a record please contact your domain provider.
    
    **Naked domain**: To point a naked domain like `example.com` to your site, simply add an A record pointing to the IP address of your site. You can get this IP by using any free online service that finds IP of sites. Try [this one](https://www.find-ip.net/ip-locator).
    
    One caveat to adding naked domains is that you will have to update the DNS record if the IP of your site changes.
    
    There are some DNS providers such as Cloudflare that allow adding CNAME records for naked domains. If so, you won't need an A record. Simply follow the same steps as in the Subdomain section above replacing `www.example.com` with `example.com`.
    
2.  After adding the DNS record, open your site dashboard.
    
3.  From the site overview page, go to **Domains** card.
4.  Click on Add Domain.
5.  Enter the custom domain.
6.  Click on Verify DNS.
7.  If the verification succeeds you have correctly added the CNAME record, and you will see Add Domain button. Click on Add Domain.
    
    [![Custom Domains](https://frappecloud.com/assets/press/images/docs/site-domain.png)](https://frappecloud.com/assets/press/images/docs/site-domain.png)
    

> Note: We obtain an SSL certificate for the custom domain. So you will be able to use HTTPS with your domain.

> You are able to add both naked and subdomains to your site [![Domains List](https://frappecloud.com/files/docs-domains-list.png)](https://frappecloud.com/files/docs-domains-list.png)

## Redirecting domains

In some cases you may not want the user the see certain domains that direct you to your site. You may even want to hide your fancy **.frappe.cloud** domain that we provide. This is also possible.

1.  You need to set one domain as primary domain. This is the domain where the "redirected domains" will redirect to

![Set Primary Image](https://frappecloud.com/files/domain-redirect.png)

2.  Next, you need to enable redirection for domains that you wish to hide

![Enable Redirect Image](https://frappecloud.com/files/domain-redirect-2.png)

That's it. Your users will be able to access your site from the redirected domains, but they will be redirected to the **primary domain** which will show up in their address bar

> This redirection will also prevent the redirected domains from appearing in search engine results.

## FAQ

#### DNS verification failed even after adding DNS record on Cloudflare

Currently the custom domains you add on FC don't work when Cloudflare proxy is enabled. Please use the **DNS only** option for your DNS record. ![Cloudflare DNS only](https://frappecloud.com/files/dns_only.png)