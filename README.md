<p align="center">به نام خدای رنگین کمان ، خداوند مهسا و نیکا ، کیان</p>
<p align="center"><img src="/asset/khoda.png?raw=true" width="300" ></p><br>

## ❝باید یه تو دهنی بزرگ به اینا بزنیم ، اینطوری نمیشه منفعل شد❞  (فرازی از بیانات [سگاروی کبیر](https://twitter.com/isegaro))


# پروژه "رویای سگارو" - تلاشی برای تحقق یک رویا
- هدف : اتصال 20 میلیون نفر به اینترنت آزاد بطور رایگان
- برای افرادی که بدلایل مالی یا نداشتن دانش فنی از دسترسی به اینترنت محروم هستند
- برای [توضیحات ساده تر اینجا](https://github.com/GFW-knocker/Segaro_Dream/tree/main/simple) را بخوانید


# راهکار
- اصلاح مدل اقتصادی v2ray از پرداخت نقدی به تبلیغات (مشابه مدل اقتصادی پروکسی های تلگرام)
- کاهش هزینه سرویس دهنده با استفاده از تکنولوژی fragment و CDN (رفع کامل دغدغه فیلتر شدن ip و دامنه)
- ساده سازی دریافت و بروزرسانی کانفیگ توسط v2rayNG با الهام از شبکه های p2p (torrent)

# مدت زمان release v1.0 (تقریبی)
- با ده برنامه نویس دو هفته
- با پنج برنامه نویس یک ماه
- یک نفر تنهایی پنج ماه


# مدل مفهومی
<p align="center"><img src="/asset/slide1.png?raw=true" width="600" ></p><br>

# ماژول Ads
- این ماژول ورق را به نفع ما برمیگرداند بعبارتی game changer هست.
- مدل اقتصادی از پرداخت نقدی که مشکلات متعدد عدم اعتماد دارد به تبلیغاتی عوض میشود (پروکسی مردم نهاد -مشابه تلگرام- دو طرف ذینفع) 
- سرویس دهنده میتواند در زمان اتصال کاربر یک notification حاوی لینک بجای نوتیف v2ray در نوار ابزار نمایش دهد 
- اپ v2ray در هر دقیقه محتویات تبلیغ را از یک فایل txt از ایپی سرویس دهنده دریافت میکند مثلا get i.i.i.i/ads.txt 
- اگر سرویس دهنده ، درخواستی از ip کاربر جهت تبلیغ دریافت نکند (کلاینت غیرمجاز) میتواند سرویس را قطع کند


# ماژول Update
- یک فایل update شامل موارد زیر است:
1. لیستی از کانفیگ ها (خصوصی یا عمومی مثل freenode)
2. ایپی های تمیز CDN (هرچند معمولا نیاز نمیشود)
3. ایپی های تمیز سایت هایی مثل یوتیوب و توییتر که کاربر بتواند مستقیم وصل شود
4. لیستی از DoH ها (خصوصی یا عمومی)
5. تنظیمات فرگمنت برای هر شهر و هر اپراتور
6. سرور های آنالیز report
7. نام سازنده فایل 
8. تاریخ ساخت فایل
9. توضیحات سازنده (تبلیغ سرور)
10. هش sha256 کل موارد فوق
- همه موارد در یک فایل json ذخیره (و با hash و امضا دیجیتال ترجیحا) منشتر میشود (حجم زیر 5KB خواهد بود)
- فایل از طریق سرویس های خیرخواهانه مثل IRCF یا خود vpn دهنده یا کانال تلگرام ، ایمیل ، و ... دریافت و اطلاعات بروز میشود.
- کاربر نیازی به دانش فنی ندارد و فایل های اپدیت در زمان اتصال اتوماتیک دریافت میشود و در زمان قطعی میتواند از کانال تلگرام یا دوست خود بگیرد
- فایل های آپدیت در سمت سرور IRCF نیز توسط بازخوردی که app کاربران میفرستد اتوماتیک بروز میشوند
- سرویس دهنده ها میتوانند برای معرفی سرور خود (و کسب درامد از تبلیغات) فایل های آپدیت را به سرور IRCF بدهند یا در شبکه های مجازی پخش کنند

# ماژول DNS
- دامنه ها ابتدا با لیست offline ایپی های تمیز مقایسه میشوند
- اگر نبود یک DNS query از طریق HTTPS و با عبور از فرگمنت به سرور DoH ارسال میشود.
- خود سرویس دهنده میتواند براحتی با یک nginx proxy pass ، همزمان DoH هم باشد.
- بدلیل داشتن فرگمنت و پشت CDN بودن ، فیلتر شدن دامنه و ip مانعی ایجاد نمیکند

# ماژول فرگمنت
- کلیه ارتباط با خارج از فرگمنت عبور میکند.
- فرگمنت به کمک DoH ، دسترسی به برخی سایت ها مثل یوتیوب را مستقیم امکان پذیر میکند
- دسترسی به تمام ایپی های کلودفلر را حتی با دامنه فیلتر شده میسر میسازد.
- در وقت و هزینه سرویس دهنده بسیار صرفه جویی میشود
- مثلا یک سرور هتزنر با 20 ترابایت ترافیک ، پشت کلودفلر به راحتی به 1000 نفر سرویس میدهد بدون تعویض ایپی و دامنه 
- تکنولوژی فرگمنت میتواند ترکیبی از این ها باشد:
1. goodbyedpi
2. powertunnel
3. greentunnel
4. gfw resist pyprox

# ماژول security (اختیاری)
- جهت حفظ امنیت کاربر از فایل های اپدیت مخرب یا DNS جعلی این ماژول کارهای زیر را انجام میدهد
1. تایید اصالت فایل اپدیت هنگام بروزرسانی
2. چک کردن اینکه دامنه های ir (یا مثلا بانک ها) در dns offline قرار نگیرند
3. ایپی کانفیگ ها و DoH ها قبل از اتصال با لیست سیاه IRCF تطبیق داده شوند


# ماژول Report 
- وظیفه این ماژول ، چک کردن وضعیت کانفیگ ها ، ip های تمیز و DoH های موجود در یک فایل آپدیت توسط app کاربر و ارسال به IRCF هست
- سرور IRCF با آنالیز اطلاعات دریافتی و بازخورد تمامی کاربران میتواند آپدیت ها (کانفیگ ها و DoH های) از کار افتاده در هر منطقه و هر اپراتور را اتوماتیک حذف کند
- و بر اساس بازخورد کاربران ، فایل های آپدیت سالم و کانفیگ های تمیز را متناسب با هر اپراتور و شهر ، اتوماتیک برای کاربر ارسال کند.
- با داشتن ماژول Report ، کلاینت کاربر هرچند ساعت یک فایل آپدیت گرفته تست کرده و به IRCF گزارش میدهد بطور خودکار.
- در نتیجه ، هم کلاینت همیشه چند کانفیگ آماده دارد (مانند پروکسی چرخشی تلگرام) و هم IRCF آمار لحظه ای از کیفیت فایل های آپدیت درگردش دارد.  


# خلاصه مدل تا اینجا : 
1. مدل درآمدی تبلیغات در v2ray اضافه شود که فقرا بتونن استفاده کنن و این بازار مکاره پرداخت نقدی جمع شود و مردم مجبور نباشن با صرف وقت و هزینه زیاد سرور شخصی بگیرن و منابع سرور بلااستفاده بماند.
2. فرگمنت و doh رو به عنوان اپشن اضافه کنیم حداقل در بعضی جاها کمک میکند مثل بازکردن یوتیوب و رد کردن sni فیلتر شده
3. دریافت تنظیمات رو ساده کنیم که در زمان قطع دسترسی ، فقط با یک پکیج ، کلیه تنظیمات دریافت شود و در زمان وصل ، کلاینت خودش ، همیشه لیستی از پکیج های فعال آماده به کار نگه دارد.
4. کلاینت ها روی هر پکیج بازخورد بدهند تا بصورت اتوماتیک پکیج ها توسط سرویس هایی مثل IRCF برای هر شهر و اپراتور رتبه بندی شوند. ( سرویس ircf رو بصورت DHT p2p هم میشه پیاده کرد distributed hash table in torrent )


# سخن پایانی
- لطفا در Discussion نظر بدید که به نظر شما چقدر شدنی هست و یا اگر راه بهتری دارید
- با تشکر از تیم IRCF که اگه این پروژه پا بگیره ، زحماتشون صد برابر میشه :))

