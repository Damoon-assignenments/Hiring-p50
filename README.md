<div dir="rtl" style="font-family: Tahoma, sans-serif; line-height: 1.6;">

<h1>🚀 تسک برنامه‌نویس بک‌اند لاراول</h1>

<h2>🎯 هدف</h2>
<p>
ارزیابی توانایی برنامه‌نویس در استفاده بهینه از <strong>Eloquent ORM</strong> برای ایجاد APIهای تمیز، ساختارمند و بهینه، با تمرکز بر استفاده از <strong>JOIN در Eloquent</strong> و <strong>Eager Loading</strong>.
</p>

<hr>

<h2>📝 توضیحات تسک</h2>
<p>لطفاً یک API در لاراول توسعه دهید که قابلیت‌های زیر را داشته باشد:</p>
<ol>
  <li><strong>ایجاد (POST)</strong> یک پکیج مسافرتی با اعتبارسنجی مناسب.</li>
  <li><strong>دریافت (GET)</strong> لیست پکیج‌های مسافرتی همراه با جزئیات رزروها با استفاده از <strong>JOIN</strong> در Eloquent و <strong>Eager Loading</strong>.</li>
  <li>پاسخ‌ها باید در قالب <strong>JSON</strong> بازگردانده شوند.</li>
  <li>اطلاعات باید در پایگاه‌داده ذخیره شوند.</li>
  <li>مستند موجود در <a href="https://platform.neshan.org/api/reverse-geocoding/" target="_blank">این لینک</a> را مطالعه کرده و در برنامه یک endpoint بسازید که:
    <ul>
      <li>مختصات ثابت <code>lat=35.6892</code> و <code>lng=51.3890</code> را به سرویس ارسال کند.</li>
      <li>خروجی دریافتی را در قالب یک فایل متنی با نام <code>output.json</code> در <strong>ریشه پروژه</strong> (<code>base_path()</code>) ذخیره کند.</li>
      <li>از API Key زیر استفاده شود:
        <pre>service.515c4e65c6284d9bb3c7a5120c03f960</pre>
      </li>
    </ul>
  </li>
  <li><strong>تسک اختیاری:</strong> نوشتن یونیت تست برای یک یا چند کنترلر/سرویس (مثلاً: TravelPackageController یا GeoService) امتیاز ویژه دارد.</li>
</ol>

<hr>

<h2>🗃️ ساختار پایگاه‌داده (MySQL)</h2>

<h3>جدول travel_packages</h3>
<ul>
  <li><strong>id</strong> (کلید اصلی)</li>
  <li><strong>name</strong> (رشته) - نام پکیج (مثلاً "تور استانبول")</li>
  <li><strong>price</strong> (اعشاری) - قیمت پکیج</li>
  <li><strong>location</strong> (رشته) - مقصد</li>
  <li><strong>created_at</strong> و <strong>updated_at</strong> (تاریخ و زمان)</li>
</ul>

<h3>جدول bookings</h3>
<ul>
  <li><strong>id</strong> (کلید اصلی)</li>
  <li><strong>package_id</strong> (کلید خارجی → travel_packages)</li>
  <li><strong>customer_name</strong> (رشته)</li>
  <li><strong>customer_email</strong> (رشته)</li>
  <li><strong>travel_date</strong> (تاریخ)</li>
  <li><strong>created_at</strong> و <strong>updated_at</strong> (تاریخ و زمان)</li>
</ul>

<hr>

<h2>💡 الزامات</h2>
<ul>
  <li>استفاده از <strong>Eloquent ORM</strong> (بدون استفاده از کوئری‌های SQL خام).</li>
  <li>تعریف روابط در مدل‌ها:
    <ul>
      <li>در مدل <strong>TravelPackage</strong> متد <code>bookings()</code> برای ارتباط یک به چند.</li>
      <li>در مدل <strong>Booking</strong> متد <code>travelPackage()</code> برای ارتباط بلعکس.</li>
    </ul>
  </li>
  <li>استفاده از <strong>with</strong> و <strong>withCount</strong> برای Eager Loading و بهینه‌سازی کوئری‌ها.</li>
  <li>متد GET باید اطلاعات زیر را بازگرداند:
    <ul>
      <li>نام پکیج، قیمت، مقصد</li>
      <li>تعداد رزروها (<code>total_bookings</code>)</li>
      <li>مشخصات مسافران (نام و ایمیل) - از طریق JOIN در Eloquent</li>
    </ul>
  </li>
  <li>در صورتی که پکیجی رزروی نداشته باشد، مقدار <code>customers</code> باید آرایه خالی <code>[]</code> باشد.</li>
</ul>

<hr>

<h2>🟢 نمونه خروجی مورد انتظار</h2>
<pre dir="ltr">
[
  {
    "id": 1,
    "name": "تور استانبول",
    "price": 1200,
    "location": "ترکیه",
    "total_bookings": 3,
    "customers": [
      { "customer_name": "علی رضایی", "customer_email": "ali@example.com" },
      { "customer_name": "زهرا احمدی", "customer_email": "zahra@example.com" }
    ]
  }
]
</pre>

<hr>

<h2>🚀 موارد تحویلی</h2>
<ul>
  <li>کد کامل API با استفاده از <strong>Eloquent ORM</strong> و روابط تعریف‌شده.</li>
  <li>اسکریپت SQL یا Migration لاراول برای ایجاد جداول و داده‌های نمونه.</li>
  <li>خروجی <code>output.json</code> پس از اجرای سرویس مختصات.</li>
  <li>فایل <strong>README</strong> شامل:
    <ul>
      <li>راهنمای راه‌اندازی پروژه (دستور اجرای migration و سرویس reverse-geocode).</li>
      <li>دستورات <code>curl</code> برای تست APIها.</li>
      <li>ذکر دقیق مدت زمان صرف‌شده برای هر بخش از تسک.</li>
    </ul>
  </li>
</ul>

<hr>

<h2>⏳ زمان و شرایط تحویل</h2>
<ul>
  <li>از زمان دریافت این تسک، <strong>24 ساعت</strong> فرصت تحویل دارید.</li>
  <li>مدت زمان واقعی صرف‌شده برای انجام تسک باید حداکثر <strong>10 ساعت</strong> باشد.</li>
  <li>یک ریپازیتوری خصوصی در GitHub بسازید و کاربر <strong>tabrizimoeen</strong> را به عنوان Collaborator اضافه کنید.</li>
</ul>

</div>
