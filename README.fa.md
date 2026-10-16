<p align="center">
<img src=".github/icon.svg" width="96" height="96" alt="Veilway">
</p>

<h1 align="center">Veilway UI</h1>

<p align="center" dir="rtl">
سیستم طراحی و ترجمه‌هایی که پنل و برنامه‌های Veilway با هم به کار می‌برند.
</p>

<p align="center">
<a href="README.md">English</a> | <b>فارسی</b>
</p>

<p align="center">
<a href="LICENSE"><img alt="license" src="https://img.shields.io/badge/license-Apache--2.0-blue"></a>
</p>

<div dir="rtl">

## این مخزن چیست

Veilway یک پلتفرم VPN متن‌باز برای کسانی است که پشت شبکه‌های سانسورشده هستند: یک هستهٔ Rust، یک پنل وب و برنامه‌های رسمی. این مخزن چیزهایی را نگه می‌دارد که پنل و برنامه‌ها روی صفحه با هم به کار می‌برند، تا همه شکل و رفتار یک محصول را داشته باشند.

- توکن‌های طراحی به شکل متغیرهای CSS. همه از یک فایل توکن ساخته می‌شوند و آزمون‌ها قاعده‌های کنتراست را روی هر رنگی که یک زمینه می‌تواند بگیرد بررسی می‌کنند.
- مادهٔ شیشه‌ای: چهار لایه (sheet، chrome، popover، dialog) که پشت هرکدام معلوم است. اگر سیستم شفافیت کمتر بخواهد یا مرورگر `backdrop-filter` نداشته باشد، سطح‌های مات جای شیشه را می‌گیرند.
- کامپوننت‌های React و نمودارها.
- اعتبارسنج پوسته. فایل پوسته فقط توکن رنگ است و مثل ورودی خصمانه با آن رفتار می‌شود: رنگ شیشه‌ای که برای پس‌زمینهٔ خودش کم‌رنگ باشد پررنگ‌تر می‌شود، و پس‌زمینه‌ای که برای متن زیادی روشن باشد رد می‌شود.
- یک برنامهٔ گالری که هر جزء را در حالت تیره و روشن، به فارسی و انگلیسی نشان می‌دهد.
- فارسی و انگلیسی، با چیدمان راست‌به‌چپ، جمع‌بستن ICU، رقم‌های فارسی و تاریخ شمسی.

</div>

<table>
<tr>
<td><img src=".github/screenshots/client-dark-en.png" width="360" alt="پنجرهٔ کلاینت، متصل، تیره، انگلیسی"></td>
<td><img src=".github/screenshots/client-light-fa.png" width="360" alt="پنجرهٔ کلاینت، متصل، روشن، فارسی"></td>
</tr>
<tr>
<td colspan="2"><img src=".github/screenshots/in-use-dark-en.png" alt="صفحهٔ گالری با پنجرهٔ کلاینت و صفحهٔ پنل، تیره، انگلیسی، سطح مات"></td>
</tr>
<tr>
<td colspan="2"><img src=".github/screenshots/in-use-light-fa.png" alt="صفحهٔ گالری با پنجرهٔ کلاینت و صفحهٔ پنل، روشن، فارسی، شفافیت کمتر"></td>
</tr>
</table>

<p align="center" dir="rtl"><sub>تصویرهایی از گالری: پنجرهٔ کلاینت در حالت تیرهٔ انگلیسی و روشن فارسی، و صفحه‌ای که پنجرهٔ کلاینت را کنار یک صفحهٔ پنل نشان می‌دهد، با سطح مات به‌جای شیشه. همهٔ نام‌ها، نشانی‌ها و عددهای این تصویرها ساختگی است (example.net).</sub></p>

<div dir="rtl">

## چه چیزهایی در آن است

| مسیر | بسته | چیست |
|---|---|---|
| `packages/ui` | `@veilway/ui` | توکن‌ها، مادهٔ شیشه‌ای، کامپوننت‌ها، نمودارها، اعتبارسنج پوسته و JSON Schema آن، و گالری. [README](packages/ui/README.md) آن شیشه و قاعدهٔ کنتراستش را توضیح می‌دهد (انگلیسی). |
| `packages/i18n` | `@veilway/i18n` | بسته‌های زبان فارسی و انگلیسی و ابزارهایی برای جهت متن، جمع‌بستن، رقم‌های فارسی و تاریخ شمسی. بدون React. |

## بررسی‌ها و گالری

همه چیز در کانتینر اجرا می‌شود و `node_modules` در volumeهای نام‌دار می‌ماند. از ریشهٔ مخزن:

</div>

```
V="-v $PWD/packages:/work/packages -v veilway-i18n-nm:/work/packages/i18n/node_modules -v veilway-ui-nm:/work/packages/ui/node_modules"
docker run --rm $V -w /work/packages/i18n node:22 sh -c "npm ci && npm run check && npm test"
docker run --rm $V -w /work/packages/ui node:22 sh -c "npm ci && npm run check && npm test && npm run build"
docker run --rm $V -w /work/packages/ui -p 127.0.0.1:5173:5173 node:22 npm run dev
```

<div dir="rtl">

دستور آخر گالری را روی `http://127.0.0.1:5173` باز می‌کند. دستور گرفتن تصویرها به یک ایمیج Playwright نیاز دارد و در [packages/ui/README.md](packages/ui/README.md) آمده است.

## قاعده‌های طراحی

فهرست کامل در [CONTRIBUTING.md](CONTRIBUTING.md) است. این‌ها قاعده‌هایی است که بیشتر از بقیه شکسته می‌شوند:

- هر تغییری که دیده می‌شود همراه با تصویر در حالت تیره و روشن، به فارسی و انگلیسی می‌آید.
- فایل پوسته و بستهٔ زبان ورودی خصمانه هستند. هر تغییر در اعتبارسنج پوسته یا بارگذار زبان همراه با آزمون‌هایی می‌آید که فایل خراب به آن می‌دهند.
- شکل قرصی (pill) ممنوع است، برچسب حروف بزرگ بالای عنوان ممنوع است، ایموجی ممنوع است، و گوشه‌ها گردی کم و یکسان دارند.
- برنامه‌ها برای یک اتصال هیچ کلمهٔ رتبه‌بندی نشان نمی‌دهند: فقط نامش را، و یک هشدار ساده اگر امن نیست.
- خط خالی درون بدنهٔ تابع نباشد، رشته‌ها با کوتیشن دوتایی، کد یک‌خطی هرجا جا شود، و هرگز ابزار قالب‌بندی کد اجرا نشود.

## وضعیت

> **نوپا.** ظاهر تأیید شده و بررسی‌ها رد می‌شوند. پنل و هر دو برنامه، دسکتاپ و اندروید، از آن استفاده می‌کنند. هزینهٔ تاری شیشه در WebView اندروید هنوز اندازه‌گیری نشده است.

## مخزن‌ها

- [veilway](https://github.com/veilway-project/veilway): هسته، API کنترل و کلاینت TypeScript آن، و برنامهٔ دسکتاپ.
- [veilway-docs](https://github.com/veilway-project/veilway-docs): مشخصات پروتکل، مرجع پیکربندی و راهنماها، به فارسی و انگلیسی. سایت آن در [veilway-project.github.io/veilway-docs](https://veilway-project.github.io/veilway-docs/fa/) است.
- veilway-ui: همین مخزن.

## مشارکت و امنیت

اول [CONTRIBUTING.md](CONTRIBUTING.md) را بخوانید. در اولین pull request از شما خواسته می‌شود یک بار [CLA](CLA.md) را امضا کنید. آسیب‌پذیری‌ها را به شکل خصوصی و طبق [SECURITY.md](SECURITY.md) گزارش کنید، هرگز در issue عمومی.

## مجوز

Apache-2.0، فایل‌های [LICENSE](LICENSE) و [NOTICE](NOTICE) را ببینید. مجوز شامل نام پروژه نمی‌شود: [TRADEMARKS.md](TRADEMARKS.md) را ببینید.

</div>
