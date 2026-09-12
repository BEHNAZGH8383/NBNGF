# سامانه مدیریت نامه‌ها

نام دانشجو: ...............

شماره دانشجویی: ...............

این پروژه یک سامانه ساده برای ورود کاربران، ارسال نامه و مشاهده کارتابل است. بک‌اند با FastAPI نوشته شده، اطلاعات در PostgreSQL ذخیره می‌شود و فرانت‌اند با HTML، CSS و JavaScript پیاده‌سازی شده است.

## امکانات پروژه

- ورود با نام کاربری و رمز عبور
- انتخاب گیرنده از بین کاربران
- ثبت موضوع، متن و یک پیوست اختیاری
- نمایش نامه‌های دریافتی و ارسالی
- مشخص‌شدن نامه خوانده‌شده
- دانلود پیوست توسط فرستنده یا گیرنده
- اجرای فرانت‌اند، بک‌اند و دیتابیس در سه Container جدا
- نگهداری دیتابیس و پیوست‌ها در Volume

## اجرای پروژه

فایل تنظیمات را از روی نمونه بسازید (فایل `.env` در Git قرار نمی‌گیرد):

```bash
cp .env.example .env
```

در PowerShell ویندوز:

```powershell
Copy-Item .env.example .env
```

سپس پروژه را اجرا کنید:

```bash
docker compose up --build -d
```

آدرس برنامه:

```text
http://localhost:8080
```

آدرس مستندات API:

```text
http://localhost:8080/api/docs
```

## حساب‌های نمونه

| نام کاربری | رمز عبور | نام |
|---|---|---|
| ali | 123456 | علی احمدی |
| sara | 123456 | سارا محمدی |
| reza | 123456 | رضا کریمی |

## ساختار پوشه‌ها

```text
backend/       کد FastAPI و تست‌ها
frontend/      فایل‌های رابط کاربری و Nginx
database/      Dockerfile دیتابیس
docs/          توضیحات پروژه و نمودارها
docker-compose.yml
```

## مسیرهای اصلی API

| روش | مسیر | کاربرد |
|---|---|---|
| POST | `/api/auth/login` | ورود کاربر |
| GET | `/api/auth/me` | اطلاعات کاربر فعلی |
| GET | `/api/users` | دریافت فهرست کاربران |
| POST | `/api/letters` | ارسال نامه |
| GET | `/api/letters/inbox` | نامه‌های دریافتی |
| GET | `/api/letters/sent` | نامه‌های ارسالی |
| GET | `/api/letters/{id}` | جزئیات نامه |
| GET | `/api/letters/{id}/attachment` | دانلود پیوست |

## تست بک‌اند

```bash
cd backend
python -m venv .venv
```

فعال‌سازی در ویندوز:

```powershell
.venv\Scripts\activate
```

فعال‌سازی در Linux یا macOS:

```bash
source .venv/bin/activate
```

نصب و اجرای تست:

```bash
pip install -r requirements-dev.txt
pytest -q
```

## وضعیت نسخه تحویلی

این نسخه علاوه بر امکانات اصلی، چک‌لیست نهایی تحویل و محتوای آماده برای برد مدیریت کار را در پوشه `docs` دارد. فایل‌های موقت تست و Cacheهای Python نیز از بسته نهایی حذف شده‌اند.

## دستورات مفید Docker

```bash
docker compose ps
docker compose logs -f backend
docker compose down
```

برای حذف کامل اطلاعات ذخیره‌شده:

```bash
docker compose down -v
```
