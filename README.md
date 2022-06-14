# Admin: Django Models-based **No Code** zero code zero learning cost management background front-end and back-end generation tools, driven by Django Restful Framework and Ant Design Pro V4

![](https://img.shields.io/pypi/v/tyadmin-api-cli)
![](https://img.shields.io/pypi/wheel/tyadmin-api-cli)

Support Python3.9! Unlimited Django version support, support the latest Django4! Support Django3!

# 🎬 Online experience demo

>Account: tyadmin Password: tyadmin

Demo address: https://tyadmin.funpython.cn/xadmin

**No Code!!! You can have a modern background management without writing a single line of code, **star**, thank you! ! **

TyAdmin: It only takes five minutes to read the README to get started quickly, no additional documentation, no framework learning cost, no need to write a line of code by yourself, fully automatic background, you deserve it!

# ✨ Features

- Automatically generate front-end and back-end management backgrounds, and the page interface is magically automatically connected. Login verification, password modification, Dashboard statistics.
- One-time possession **Add, delete, modify, search, filter, search, export data in full, choose to export**
- **Foreign key fields, many-to-many fields, rich text, files, pictures, django's own permission system**

Just design the model, configure which models need to be generated in the settings, and run the command: [Quick Start](#Quick Start)

>The backend generates a django app to the project directory, just register it, no need to write another line of code! The code is under your control, and there is no obstruction to secondary development!
> The front-end generates an Ant Design Pro V4 project, which only needs to be started once, without writing a single line of code! The code is under your control, and there is no obstruction to secondary development!

Front-end pages, back-end interfaces, routing, and menus are all automatically connected. You only need to copy documents, modify configurations, and do not need to write a line of code! !
# Quick start 🤟

📨 Interactive exchange feedback QQ group: 304094780

>Existing projects can start from the second step, pay attention to modify the GEN_APPS variable for the list of apps you need to generate
>If you have any questions, you can compare the tyadmin_demo_finish project under demos to find your own differences, and check the [QA link] (#QA link)

## 1. Download the demo project installation dependencies (Note!! If you have projects that do not need to download the demo project, you can start from the second step, pay attention to modifying the GEN_APPS variable to the list of apps you need to generate)

````
git clone https://github.com/mtianyan/tyadmin_api_cli.git
cd tyadmin_api_cli/demos/tyadmin_demo_init
# Install the dependencies that the project originally needs
pip install -r requirement.txt
````

## 2. Install tyadmin-api-cli and register tyadmin-api-cli

```diff
pip install tyadmin-api-cli

INSTALLED_APPS = [
+    'captcha',
+    'tyadmin_api_cli',
]

+TY_ADMIN_CONFIG = {
+    'GEN_APPS': ['demo']
+}

# easy to copy

    'captcha',
    'tyadmin_api_cli',

TY_ADMIN_CONFIG = {
    'GEN_APPS': ['demo']
}
```
GEN_APPS: Fill in the list of apps you want to generate.

## 3. Initialize back-end app (tyadmin_api) + front-end project (tyadmin) && generate back-end automated views, filters, routes, sequencers + front-end pages and routing menus

To generate back-end page dependencies, you need to install Node.js -> https://www.runoob.com/nodejs/nodejs-install-setup.html

>Install Node.js 10 or above, the recommended installation version Latest LTS Version: 12.19.0

````
python manage.py init_admin && python manage.py gen_all && cd tyadmin && npm install && npm run build
````

> Wait patiently for a while, build will output the front-end page to the templates folder, generate the front-end js, css and wait until the static folder

## 4. Register the generated django app

````diff
INSTALLED_APPS = [
    'captcha',
    'tyadmin_api_cli',
+ 'tyadmin_api'
]

# easy to copy

'tyadmin_api'
````

## 5. Register homepage routing, api routing

./tyadmin_demo/urls.py

````diff
+ from tyadmin_api.views import AdminIndexView

urlpatterns = [
+ re_path('^xadmin/.*', AdminIndexView.as_view()),
+ path('api/xadmin/v1/', include('tyadmin_api.urls')),
]

# easy to copy
from tyadmin_api.views import AdminIndexView

re_path('^xadmin/.*', AdminIndexView.as_view()),
path('api/xadmin/v1/', include('tyadmin_api.urls')),
```

