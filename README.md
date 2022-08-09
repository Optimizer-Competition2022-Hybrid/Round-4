# Round-4

<p align="center">
  <a href="" rel="noopener">
 <img width="150" src="http://optimizer.math.sharif.edu/wp-content/uploads/2021/02/optimizer.png" alt="Optimizer logo"></a>
</p>
<h3 align="center">Hybrid</h3>

<div align="center">

  [![Status](https://img.shields.io/badge/status-active-success.svg)]() 
  [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/mtefagh/demos/HEAD)
  [![License](https://img.shields.io/badge/license-GPL-blue.svg)](https://github.com/mtefagh/demos/blob/master/LICENSE)

</div>

---

## 📝 فهرست مطالب
- [صورت‌بندی سوال](#problem_statement)
- [الگوریتم بهینه‌سازی](#idea)
- [محدودیت‌ها](#limitations)
- [ایده‌های گسترش](#future_scope)
- [روند اجرا](#getting_started)
- [نحوه استفاده](#usage)
- [وابستگی‌ها](#tech_stack)
- [نویسندگان](#authors)
- [قدردانی](#acknowledgments)

## 🧐 صورت‌بندی سوال <a name = "problem_statement"></a>
فرمول‌بندی سوال بهینه‌سازی حل شده در کد و اشاره به تقریب‌هایی که از سوال اصلی زده‌اید تا به سوال مورد نظر برسید

## 💡 الگوریتم بهینه‌سازی <a name = "idea"></a>
در ابتدا برای پیدا کردن subsetهای مورد نظر از الگوریتم `DBSCAN` استفاده می‌کنیم.
تنظیم مقدار `epsilon` و `min sample` نیز توسط جست‌وجوی دودویی بر حسب تعداد outlierها انجام می‌شود
به طوری که تعداد clusterها بیشینه باشد.
<br>
سپس اگر تعداد منیفولدها از تعداد منیفولدهای مورد نظر بیشتر پیشبینی شده بود به کمک تابع `is_manifold`
(که خود بر اساس بعد local داده‌ها کار می‌کند)
به دنبال دو منیفولد می‌گردیم که از نظر ساختار بعدی مشابه با هم باشند تا آن‌ها را با هم merge کنیم.
<br>
در مرحله بعد برای جدا کردن subsetهایی که دارای بیش از یک منیفولد هستند
ابتدا الگوریتم `LLE` را بر روی subset اجرا می‌کنیم و داده را به بعد پایین‌تر می‌بریم.
از آنجایی که بعد ذاتی داده‌ها پایین بود می‌توان بعد مقصد را عدد کوچکی مانند ۳ انتخاب کرد تا
هم قابلیت نمایش داشته باشد و هم اطلاعات مربوط به داده تا حد ممکن حفظ شود.
در نهایت برای جداسازی منیفولدها می‌توان از `Spectral clustering` استفاده کرد اما به علت سرعت پایین آن از 
ورژن خاصی از `dfs` در `ComponentScan` استفاده کردیم تا مولفه‌های همبندی را بیابیم.
<br>
با کاهش بعد داده‌های subsetها امکان اجرای الگوریتم‌های کلاسیک clustering فراهم می‌شود
و می‌توان برای یافت clusterها و جدا کردن منیفولدها از آن‌ها استفاده کرد.
<br>
برای تخمین بعد ذاتی داده‌ها از تابع `get_dim` استفاده می‌کنیم که با بررسی میزان حفظ locality در بعدهای مختلف `LLE`
بعد اصلی را تحمین می‌زند.

## ⛓️ محدودیت‌ها <a name = "limitations"></a>
برنامه به طور خاص بر حسب visualization و ساختار داده‌های این مرحله نوشته شده لذا ممکن است برای اجرا بر روی انواع داده‌های دیگر نیاز به تغییراتی غیرخودکار داشته باشد. 
در حالت کلی می‌توان از فایل `Optimization_general.ipynb` شروع کرد و تغییرات خاص برای هر نوع داده را لحاظ کرد.

## 🚀 ایده‌های گسترش <a name = "future_scope"></a>


## 🏁 روند اجرا <a name = "getting_started"></a>
تکه کدها از بالا به پایین در jupyter notebook مرتب شده‌اند و قابل اجرا هستند.

### پیش‌نیازها

برای نصب پیش‌نیازها کافی است دستور زیر را اجرا کنید. 
```
pip install -r pip-requirements
```

## 🎈 نحوه استفاده <a name="usage"></a>
ابتدا فایل ورودی را در پوشه‌ی اجرا قرار دهید سپس مقدار متغییر subtask را در نوت‌بوک به سابتسک مورد نظر تغییر دهید.
<br>
برای زیرمسئله‌های ۳ و ۴ می‌توان از راه حل کلی ارائه شده در
<a href="https://github.com/Optimizer-Competition2022-Hybrid/Round-4">اینجا</a>
استفاده نمود. (که البته برای کارکرد بهینه نیار به بررسی‌های جداگانه و غیرخودکار دارد)
## ⛏️ وابستگی‌ها <a name = "tech_stack"></a>
زبان برنامه‌نویسی:
Python
<br>
لیست کتاب‌خانه‌های استفاده شده:

```
miniballCpp
matplotlib
pandas
numpy
scikit-learn
scipy
```

## ✍️ نویسندگان <a name = "authors"></a>
بهنام روحانی، امیرسالار صفایی‌قادری، مانی حاجی‌مهدی

## 🎉 قدردانی <a name = "acknowledgments"></a>
تشکر از کسانی که به نحوی در برگزاری این مسابقه سهیم بوده‌اند
