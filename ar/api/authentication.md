## المصادقة

ستحتاج إلى استخدام رؤوس HTTP الخاصة بـ "التفويض" و "X-Press-Team" لاستخدام Frappe Cloud API.

نظرًا لأنك قد تكون عضوًا في فرق متعددة على Frappe Cloud ، فمن الضروري تعيين الفريق باستخدام رأس "X-Press-Team".

راجع [API / إنشاء رمز وصول](https://frappecloud.com/docs/api/create_an_access_token) لإنشاء مفتاح API وسر API.

""
التفويض: رمز <api-key>: <api-secret>
X-Press-Team: <فريق>
""

**طلب**

""
طلبات الاستيراد

رؤوس = {
    "التفويض": "رمز <api-key>: <api-secret>" ،
    "X-Press-Team": "<team>"
}
request.get ("https://frappecloud.com/api/method/press.api.account.me"، headers = headers) .json ()
""

**إجابة**

""
{
  "رسالة": {
    "المستخدم": "<user>"،
    "فريق": "<team>"
  }
}
""