# الوصول إلى قاعدة البيانات

> الوصول إلى قاعدة البيانات متاح للمواقع بسعر 50 دولارًا أمريكيًا وما فوق الخطط

سيكون لديك الآن وصول كامل إلى قاعدة بيانات موقعك.

## تمكين الوصول إلى قاعدة البيانات

انتقل إلى Site Dashboard> Database> Access.

![تمكين الوصول إلى قاعدة البيانات](https://frappecloud.com/files/database-access-enable.png)

انقر فوق تمكين الوصول إذا لم تكن قد استخدمت هذه الميزة مسبقًا. سترى الآن بيانات الاعتماد لتوصيل قاعدة البيانات الخاصة بك.

![بيانات اعتماد الوصول إلى قاعدة البيانات](https://frappecloud.com/files/database-access-credentials.png)

## الاتصال بقاعدة البيانات

### أداة التحليلات أو ذكاء الأعمال

انسخ بيانات الاعتماد الموضحة إلى أداة التحليلات الخاصة بك.

نحن نسمح باتصالات TLS فقط. إذا كنت تواجه مشكلات أثناء الاتصال ، فيرجى التأكد من أن أداة التحليلات تستخدم SSL / TLS وشهادتنا [chain.pem](https://frappecloud.com/files/chain.pem) لـ "\* .hisab.cloud (توقيع [Let's Encrypt](https://letsencrypt.org/)).

### عميل سطر أوامر MariaDB / MySQL

![قاعدة البيانات CLI](https://frappecloud.com/files/database-access-cli.png)

انسخ الأمر إلى وحدة التحكم الخاصة بك والصق كلمة المرور عند مطالبتك بذلك.

ستحتاج إلى تثبيت [mariadb-client أو mysql-client](https://mariadb.com/docs/server/connect/clients/mariadb-client/) على جهازك.

> لديك الآن وصول \*\* للقراءة والكتابة \*\* إلى قاعدة البيانات الخاصة بك. أي تغييرات يتم إجراؤها على قاعدة البيانات الخاصة بك ستكون دائمة.

## الأسئلة الشائعة: لا يمكن الاتصال بقاعدة البيانات من PowerBI

إذا لم ينجح الاتصال بـ PowerBI ، فربما تستخدم MySQL Connector. نستخدم MariaDB لقواعد البيانات الخاصة بنا. يرجى استخدام موصل Mariadb مع PowerBI لنفسه. يمكنك العثور على مستندات لنفس [هنا](https://mariadb.com/resources/blog/getting-started-with-the-mariadb-direct-query-adapter-for-microsoft-power-bi/).
