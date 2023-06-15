## Billing

## Summary of Invoices

This API returns a list of invoices (both Paid and Unpaid) for the given team in descending order of creation date. The invoices also contain a list of line items (`items` in API) for that invoice.

### Endpoint

`/api/method/press.api.billing.get_summary`

### Request

```
import requests

headers = {
    "Authorization": "Token <api-key>:<api-secret>",
    "X-Press-Team": "<team>"
}
requests.get("https://frappecloud.com/api/method/press.api.billing.get_summary", headers=headers).json()
```

> All requests require `Authorization` and `X-Press-Team` headers.

### Sample Response Data:

```
{
    "message": [
        {
            "name": "INV-2022-00106",
            "status": "Paid",
            "period_end": "2022-07-31",
            "payment_mode": "Card",
            "type": "Subscription",
            "currency": "INR",
            "amount_paid": 750.0,
            "items": [
                {
                    "amount": 750.0,
                    "name": "whatsapp.frappe.cloud",
                    "type": "Site",
                    "parent": "INV-2022-00106",
                    "quantity": 30.0,
                    "rate": 25.0,
                    "plan": "USD 25"
                }
            ]
        }
    ]
}
```