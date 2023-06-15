## تكوين الموقع

[تكوين الموقع](https://frappeframework.com/docs/v13/user/en/basics/sites#site-config) هي طريقة Frappe Framework لتحديد متغيرات البيئة.

يتيح لك تكوين الموقع تكوين الخيارات الخاصة بموقع واحد.

على سبيل المثال

* تكوين حساب بريد إلكتروني لإرسال رسائل بريد إلكتروني منها.
* تعطيل ذاكرة التخزين المؤقت لموقع الويب
* تعطيل [البحث العام](https://docs.erpnext.com/docs/user/manual/en/using-erpnext/Global-search)
* تمكين [البرامج النصية للخادم](https://docs.erpnext.com/docs/user/manual/en/customize-erpnext/server-script)

## تحديث تكوين الموقع

1. انتقل إلى علامة التبويب ** Site Config **.
2. أدخل القيم في حقل الإدخال المقابل.
3. انقر فوق ** تحديث التكوين **.

[![تهيئة الموقع](https://frappecloud.com/assets/press/images/docs/site-config.png)](https://frappecloud.com/assets/press/images/docs/site-config .بي إن جي)

## التعليمات

## لماذا لا يمكنني تمكين المطور \ _mode؟

عند تمكين وضع المطور ، يتم إنشاء ملفات JSON عند إنشاء أي مستندات قياسية على سبيل المثال ، DocType و Page و Report و Workspace وما إلى ذلك. يجب أن تكون ملفات JSON هذه جزءًا من التطبيق. لا يمكنك إضافة هذه الملفات إلى تطبيقات Frappe و ERPNext القياسية ، سوف تحتاج إلى إنشاء التطبيق الخاص بك. لهذا السبب لا يمكنك تمكين وضع المطور على Frappe Cloud. يجب عليك إنشاء هذه الميزات كجزء من تطبيق مخصص ثم تحميلها على Frappe Cloud لاستخدامها.