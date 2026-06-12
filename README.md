# Nova Skills

وب‌اپلیکیشنی برای آموزش آنلاین با قابلیت‌های کلاس‌درس مجازی

## نصب

### پیش‌نیازها
- Python 3.8+
- PostgreSQL (اختیاری)
- Redis (برای WebSocket)

### مراحل نصب

1. مخزن را کلون کنید:
```bash
git clone https://github.com/Liam9103/nova-skills.git
cd nova-skills
```

2. محیط مجازی را ایجاد کنید:
```bash
python -m venv venv
source venv/bin/activate  # در Windows: venv\Scripts\activate
```

3. وابستگی‌ها را نصب کنید:
```bash
pip install -r requirements.txt
```

4. فایل `.env` را ایجاد کنید:
```bash
cp .env.example .env
```

5. مهاجرت دیتابیس را انجام دهید:
```bash
python manage.py migrate
```

6. سوپرکاربر را ایجاد کنید:
```bash
python manage.py createsuperuser
```

7. سرور را اجرا کنید:
```bash
python manage.py runserver
```

## ویژگی‌ها

### احراز هویت
- ثبت‌نام دانشجو و استاد
- ورود و خروج
- مدیریت پروفایل

### کلاس‌درس
- ایجاد کلاس توسط استاد
- ثبت‌نام دانشجویان
- چت زنده
- لیست کاربران (استاد و دانشجویان)
- مدیریت میکروفون و دوربین
- بالا بردن دست برای پرسش
- اشتراک صفحه استاد
- گفتگوی خصوصی

### فایل‌ها و پروژه‌ها
- ایجاد پروژه‌ با دسته‌بندی
- آپلود فایل‌های کلاسی
- دانلود فایل‌ها
- فیلتر پروژه‌ها براساس دسته‌بندی
- حذف پروژه و فایل

## مسیرهای API

### احراز هویت
- `POST /api/auth/register/` - ثبت‌نام
- `POST /api/auth/login/` - ورود
- `POST /api/auth/logout/` - خروج
- `GET /api/auth/profile/` - دریافت پروفایل

### کلاس‌درس
- `POST /api/classroom/create/` - ایجاد کلاس
- `GET /api/classroom/list/` - لیست کلاس‌ها
- `GET /api/classroom/<id>/` - دریافت کلاس
- `POST /api/classroom/<id>/enroll/` - ثبت‌نام در کلاس
- `POST /api/classroom/<id>/activate/` - فعال کردن کلاس
- `POST /api/classroom/<id>/deactivate/` - غیرفعال کردن کلاس
- `POST /api/classroom/<id>/message/` - ارسال پیام
- `GET /api/classroom/<id>/messages/` - دریافت پیام‌ها
- `GET /api/classroom/<id>/students/` - لیست دانشجویان و استاد

### فایل‌ها و پروژه‌ها
- `POST /api/files/projects/<classroom_id>/create/` - ایجاد پروژه
- `GET /api/files/projects/<classroom_id>/list/` - لیست پروژه‌ها
- `DELETE /api/files/projects/<project_id>/delete/` - حذف پروژه
- `POST /api/files/classroom/<classroom_id>/upload/` - آپلود فایل
- `GET /api/files/classroom/<classroom_id>/list/` - لیست فایل‌ها
- `DELETE /api/files/<file_id>/delete/` - حذف فایل
- `GET /api/files/<file_id>/download/` - دانلود فایل

## ساختار پروژه

```
nova-skills/
├── manage.py
├── requirements.txt
├── .env.example
├── nova_skills/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   ├── asgi.py
│   └── wsgi.py
└── apps/
    ├── authentication/
    │   ├── models.py
    │   ├── views.py
    │   ├── serializers.py
    │   ├── urls.py
    │   └── admin.py
    ├── classroom/
    │   ├── models.py
    │   ├── views.py
    │   ├── serializers.py
    │   ├── urls.py
    │   ├── consumers.py
    │   ├── routing.py
    │   └── admin.py
    └── files/
        ├── models.py
        ├── views.py
        ├── serializers.py
        ├── urls.py
        └── admin.py
```

## مجوزها

این پروژه تحت لیسانس MIT منتشر شده است.
