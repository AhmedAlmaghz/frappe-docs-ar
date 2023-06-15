## المواقع

تتطلب جميع الطلبات عناوين "التفويض" و "X-Press-Team".

""
طلبات الاستيراد

رؤوس = {
    "التفويض": "رمز <api-key>: <api-secret>" ،
    "X-Press-Team": "<team>"
}
request.get ("https://frappecloud.com/api/method/press.api.account.me"، headers = headers) .json ()
""

ومع ذلك ، من أجل الإيجاز ، يتم تمثيل المقتطف أعلاه كـ

""
request.get ("https://frappecloud.com/api/method/press.api.account.me")
""

### قائمة بجميع المواقع

**طلب**

""
request.get ("https://frappecloud.com/api/method/press.api.site.all")
""

**إجابة**

""
{
    "رسالة": [
        {
            "الاسم": "مشتركة"،
            "مشتركة": صحيح ،
            "الحالة": "نشط"،
            "المواقع": [
                {
                    "الاسم": "site-1.erpnext.com" ،
                    "الحالة": "نشط"،
                    "مقاعد البدلاء": "مقاعد البدلاء-0198-002761-f3"
                }
            ]
        } ،
        {
            "الاسم": "مقاعد البدلاء-0000" ،
            "العنوان": "الإصدار 13"،
            "الإصدار": "الإصدار 13"،
            "مقاعد": [
                {
                    "الاسم": "مقاعد البدلاء-0000-000000-f0" ،
                    "الحالة": "نشطة"
                }
            ] ،
            "المواقع": [
                {
                    "الاسم": "site-2.frappe.cloud" ،
                    "الحالة": "نشط"،
                    "مقاعد البدلاء": "مقاعد البدلاء-0000-000000-f0"
                }
            ]
        }
    ]
}
""

### الحصول على موقع

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.get"، json = data)
""

**إجابة**

""
{
    "رسالة": {
        "الاسم": "site-0.frappe.cloud" ،
        "الحالة": "نشط"،
        "frappe_version": "الإصدار 13"،
        "server_region_info": {
            "العنوان": "كيب تاون ، جنوب إفريقيا"
        }
    }
}
""

### احصل على خيارات لإنشاء موقع

""
request.get ("https://frappecloud.com/api/method/press.api.site.options_for_new")
""

**إجابة**

""
{
    "رسالة": {
        "الخطط": [
            {
                "الاسم": "10 دولارات أمريكية"
            } ،
            {
                "الاسم": "25 دولارًا أمريكيًا"
            }
        ] ،
        "الإصدارات": [
            {
                "الاسم": "الإصدار 13"،
                "مجموعات": [
                    {
                        "الاسم": "مقاعد البدلاء-0001" ،
                        "العنوان": "الإصدار 13"،
                        "تطبيقات": [
                            {
                                "التطبيق": "فرابي"،
                                "repository_url": "https://github.com/frappe/frappe"،
                                "الفرع": "الإصدار 13"
                            } ،
                            {
                                "التطبيق": "erpnext"،
                                "repository_url": "https://github.com/frappe/erpnext"،
                                "الفرع": "الإصدار 13"
                            }
                        ] ،
                        "عناقيد المجموعات": [
                            {
                                "الاسم": "مومباي"
                            } ،
                            {
                                "الاسم": "فرانكفورت"
                            } ،
                            {
                                "الاسم": "البحرين"
                            } ،
                            {
                                "الاسم": "كيب تاون"
                            } ،
                            {
                                "الاسم": "N. Virginia"
                            }
                        ]
                    }
                ]
            }
        ]
    }
}
""

### إنشاء موقع

**طلب**

""
البيانات = {
    "موقع": {
        "الاسم": "الموقع 0"،
        "تطبيقات": [
            "فرابي"،
            "erpnext"
        ] ،
        "المجموعة": "مقاعد البدلاء-0001"،
        "الكتلة": "كيب تاون" ،
        "الخطة": "10 دولارات أمريكية"،
    }
}

request.post ("https://frappecloud.com/api/method/press.api.site.new"، json = data)
""

**إجابة**

""
{
    "رسالة": {
        "site": "site-0.frappe.cloud" ،
        "الوظيفة": "0000000000"
    }
}
""

سوف تتلقى على الفور ردًا على هذا الطلب ، مع اسم الموقع. يمكنك بعد ذلك استطلاع حالة الموقع باستخدام [الحصول على موقع](https://frappecloud.com/docs/api/sites#get-a-site). يمكن استخدام الموقع بعد أن تكون حالة الموقع "نشطة".

### إسقاط موقع

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.archive"، json = data)
""

**إجابة**

""
{}
""

### إلغاء تنشيط الموقع

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.deactivate"، json = بيانات)
""

**إجابة**

""
{}
""

### تنشيط موقع

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.activate"، json = data)
""

**إجابة**

""
{}
""

### سرد كافة النسخ الاحتياطية

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.backups"، json = data)
""

**إجابة**

""
{
    "رسالة": [
        {
            "with_files": 1 ،
            "database_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-database.sql.gz" ،
            "private_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-private-files.tar"،
            "public_url": "https://site-0.frappe.cloud/backups/00000000_000000-site-0_frappe_cloud-files.tar" ،
            "الإنشاء": "0000-00-00 00: 00: 00.000000"،
            "خارج الموقع": 1
        }
    ]
}
""

### جدولة النسخ الاحتياطي

**طلب**

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.backup"، json = data)
""

**إجابة**

""
{}
""

### تسجيل الدخول كمسؤول

""
البيانات = {
    "الاسم": "site-0.frappe.cloud" ،
}

request.post ("https://frappecloud.com/api/method/press.api.site.login"، json = data)
""

**إجابة**

""
{
    "الرسالة": "00000000000000000000000000000000000000000000000000000000"
}
""

يمكنك استخدام الرد كملف تعريف ارتباط جانبي لتسجيل الدخول إلى موقعك

""
ملفات تعريف الارتباط = {
    "sid": "00000000000000000000000000000000000000000000000000000000"،
}

request.post ("https://site-0.frappe.cloud/api/method/frappe.auth.get_logged_user" ، ملفات تعريف الارتباط = ملفات تعريف الارتباط) .json ()
# {'message': 'المسؤول'}
""