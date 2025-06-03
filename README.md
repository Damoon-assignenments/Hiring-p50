<div dir="rtl" style="font-family: Tahoma, sans-serif; line-height: 1.6;">

# 🚀 تسک برنامه‌نویس بک‌اند لاراول

## 🎯 هدف
ارزیابی توانایی برنامه‌نویس در استفاده بهینه از <strong>Eloquent ORM</strong> برای ایجاد APIهای تمیز و بهینه، با تمرکز بر استفاده از <strong>JOIN</strong> در Eloquent و بهینه‌سازی کوئری‌ها با استفاده از <strong>Eager Loading</strong>.

---

## 📝 توضیحات تسک
یک API در لاراول توسعه دهید که قابلیت‌های زیر را داشته باشد:
<ol>
  <li><strong>ایجاد (POST)</strong> یک پکیج مسافرتی.</li>
  <li><strong>دریافت (GET)</strong> لیست پکیج‌های مسافرتی همراه با جزئیات رزروها با استفاده از <strong>JOIN</strong> در Eloquent.</li>
  <li>پاسخ‌ها باید در قالب <strong>JSON</strong> برگردانده شوند.</li>
  <li>از <strong>اعتبارسنجی (Validation)</strong> لاراول برای عملیات ایجاد (Create) استفاده شود.</li>
  <li>نتایج باید در دیتابیس ذخیره شوند.</li>
   <li>نتایج باید در دیتابیس ذخیره شوند.</li>
    <li>مستند موجود در <a href="https://platform.neshan.org/api/reverse-geocoding/" target="_blank">این لینک</a> را مطالعه و در برنامه در قالب یک endpoint با طول و عرض جغرافیایی ثابت فراخوانی کن و خروجی سرویس را در قالب یک فایل متنی با نام output.json در root پروژه ذخیره کن. 
APIKey: service.515c4e65c6284d9bb3c7a5120c03f960
</li>

  <li><strong>تسک اختیاری:</strong> نوشتن یونیت تست برای سرویس‌ها امتیاز ویژه خواهد داشت</li>
</ol>

---

## ⏳ زمان و شرایط تحویل
<ul>
  <li>از زمان ارسال لینک، 24 ساعت فرصت برای تحویل تسک وجود دارد.</li>
  <li>مدت زمان انجام تسک نباید بیش از 10 ساعت باشد.</li>
  <li>یک ریپازیتوری خصوصی در گیت‌هاب ایجاد کرده و کاربر <strong>tabrizimoeen</strong> را به عنوان همکار (Collaborator) اضافه کنید.</li>
  <li>در فایل <strong>README</strong> پروژه:
    <ul>
      <li> توضیحات مورد نیاز برای راه‌اندازی صحیح پروژه را قرار دهیدو curl فراخوانی سرویس‌ها</li>
      <li>زمان صرف شده برای هر بخش تسک را به طور دقیق ذکر کنید.</li>
    </ul>
  </li>
</ul>

---

## 🗃️ ساختار پایگاه‌داده (MySQL)
جدول‌های زیر را ایجاد کنید:

### travel_packages
- <strong>id</strong> (کلید اصلی)
- <strong>name</strong> (رشته) - نام پکیج (مثلاً "تور استانبول")
- <strong>price</strong> (اعشاری) - قیمت پکیج
- <strong>location</strong> (رشته) - مقصد
- <strong>created_at</strong> و <strong>updated_at</strong> (تاریخ و زمان)

### bookings
- <strong>id</strong> (کلید اصلی)
- <strong>package_id</strong> (کلید خارجی -> travel_packages)
- <strong>customer_name</strong> (رشته) - نام مسافر
- <strong>customer_email</strong> (رشته) - ایمیل مسافر
- <strong>travel_date</strong> (تاریخ)
- <strong>created_at</strong> و <strong>updated_at</strong> (تاریخ و زمان)

---

## 💡 الزامات
<ul>
  <li>استفاده از <strong>Eloquent ORM</strong> و عدم استفاده از کوئری‌های خام (Raw SQL).</li>
  <li>تعریف روابط در مدل‌ها:
    <ul>
      <li>در مدل <strong>TravelPackage</strong> متد <strong>bookings</strong> برای ارتباط "یک به چند" ایجاد شود.</li>
      <li>در مدل <strong>Booking</strong> متد <strong>travelPackage</strong> برای ارتباط بلعکس ایجاد شود.</li>
    </ul>
  </li>
  <li>از <strong>Eager Loading</strong> با استفاده از <strong>with</strong> و <strong>withCount</strong> برای بهینه‌سازی عملکرد استفاده شود.</li>
  <li>متد GET باید اطلاعات زیر را برگرداند:
    <ul>
      <li>نام پکیج، قیمت، مقصد</li>
      <li>تعداد رزروها</li>
      <li>مشخصات مسافران (با استفاده از JOIN در Eloquent)</li>
    </ul>
  </li>
</ul>

---

## 🟢 نمونه خروجی مورد انتظار
<pre dir="ltr">
[
    {
        "id": 1,
        "name": "تور استانبول",
        "price": 1200,
        "location": "ترکیه",
        "total_bookings": 3,
        "customers": [
            {"customer_name": "علی رضایی", "customer_email": "ali@example.com"},
            {"customer_name": "زهرا احمدی", "customer_email": "zahra@example.com"}
        ]
    }
]
</pre>

---

## 🚀 موارد تحویلی
<ul>
  <li>کد کامل API با استفاده از <strong>Eloquent ORM</strong> و JOIN.</li>
  <li>اسکریپت SQL برای ایجاد جداول و داده‌های نمونه.</li>
</ul>
</div>
