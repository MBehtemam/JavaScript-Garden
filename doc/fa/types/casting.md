## تبدیل نوع 

جاوااسکریپت یک زبان نوع ضعیف است، بنابراین هر جا **نیاز** باشد باید از تبدیل نوع استفاده کرد

    // These are true
    new Number(10) == 10; // Number.toString() is converted
                          // back to a number

    10 == '10';           // Strings gets converted to Number
    10 == '+10 ';         // More string madness
    10 == '010';          // And more 
    isNaN(null) == false; // null converts to 0
                          // which of course is not NaN
    
    // These are false
    10 == 010;
    10 == '-10';

> **ES5 Note:**اعدادی که با `0` شروع می شوند  به عنوان اکتال شناخته می شود
> و این پشتیبانی در ES5 برداشته شده است
برای دوری از این موضوع استفاده از [strict equal operator](#types.equality)  پیشنهاد می شود.

### Constructors of Built-In Types

سازنده های تو کار مانند `Number` و `String` زمانی که با کلمه کلیدی `new` به کاربرده می شوند نسبت به زمانی که بدون این کلمه کلیدی بکار برده می شوند رفتار متفاوتی دارند

    new Number(10) === 10;     // False, Object and Number
    Number(10) === 10;         // True, Number and Number
    new Number(10) + 0 === 10; // True, due to implicit conversion

اگر از `Number` به همراه کلمه کلیدی `new` استفاده شود یک شی از نوع  `Number` ساخته می شود اما اگر همین نوع بدون کلمه `new` استفاده شود به عنوان یک تبدیل کننده نوع رفتار می کنند.



روش های زیر از بهترین روش های تبدیل نوع هستند

### تبدیل به رشته 

    '' + 10 === '10'; // true

با اضافه کردن یک رشته خالی عدد به رشته تبدیل می شود

### تبدیل به نوع عدد

    +'10' === 10; // true

استفاده از عملگر `unarray` یک رشته را به عدد تبدیل می کند

### تبدیل به بولین

استفاده دوبار از عملگر `not` باعث می شود یک مقدار به بولین تبدیل شود

    !!'foo';   // true
    !!'';      // false
    !!'0';     // true
    !!'1';     // true
    !!'-1'     // true
    !!{};      // true
    !!true;    // true


