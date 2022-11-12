<div align="center">
	
# שאלות הכנה לראיון עבודה בNodeJS אהבתם ? תנו ⭐
</div>

<div dir="rtl">
	
| מספר      | שאלה |
| ----------- | ----------- |
| 1      | [מה זה Node.JS ?](#ש-מה-זה-nodejs-)       |
| []()      | 2       |
| []()      | 3       |
| []()      | 4       |
| []()      | 5       |
| גשדגשגשדגש   | 2        |

	
</div>

## ש. מה זה Node.JS ?

ת.NodeJS היא סביבת ריצה של Javascript שבנויה על מנוע הJavascript של גוגל - מנוע V8.
נוד היא סביבת ריצה מונחת אירועים (event driven) שבה פקודות פלט קלט (I/O) רצות באופן אסינכרוני , דבר שהופך אותה לקלה,יעילה וסקלבילית  (scaleable).


## ש. מהי ארכיטקטורה מונחת אירועים (Event Driven Architecture) ?

ארכיטקטורה מונחת אירועים משתמשת באירועים כדי להפעיל פונקציות שונות. אירוע יכול להיות כל דבר, כגון לחיצה על מקש במקלדת או לחיצה על כפתור עכבר שבוצע ע"י המשתמש או המערכת.

## ש.מה הופך את Node.JS לטובה יותר מפריימוורקים אחרים ?

ת.
* Node.JS מספקת פשטות בפיתוח כתוצאה מהאופן בו היא פועלת - לא חוסמת פעולות I.O וכן מודל מונחה אירועים כאמור , דבר המביא לזמן תגובה קצר ועיבוד מקבילי , שלא כמו פריימוורקים אחרים שמצריכים את המפתח לנהל תהליכונים. 

* היא רצה כאמור על מנוע V8 של גוגל שכתוב בC++ , שהוא בעל ביצועים גבוהים ושיפור מתמיד.

* מאחר ואנחנו משתמשים בJavascript גם בפרונטאנד וגם בבקאנד גורמת לכך שעקומת הלמידה מהירה יותר , וכן הפיתוח מהיר יותר.

* כמות ספריות עצומה , משמע איננו צריכים להמציא את הגלגל

## ש. איך עובד Node.js ? 
ת. כאמור Node.js היא מונחת אירועים. בעקרון הסרבר מורכב מתהליכון יחיד המעבד אירוע אחר אירוע.
בקשה חדש (request) נחשבת גם היא אירוע. הסרבר מתחיל לעבד את הבקשה וכאשר ישנה אופרציה חוסנת ( blocking i.o ) , הסרבר לא מחכה עד לסיום ביצוע הבקשה אלא רושם פוקצית Callback. הסרבר באופן מיידי מתחיל לעבד עוד אירועים . כאשר האופרציה החוסמת מסיימת , שזה אירוע (event) בשם עצמו , השרת ימשיך לעבד את הבקשה ע"י ביצוע הcallback ברגע שיש לו זמן .

<br>

![image](https://user-images.githubusercontent.com/37695804/200107939-27d3994e-a53a-42b6-bb77-bc44237d6861.png)

<br>

תהליך העיבוד באמצעות תהליכון יחיד וEVENT LOOP :
*	הלקוח שולח בקשה לשרת.
*	שרת הנוד מתחזק Thread Pool עם מספר תהליכונים מוגבל ע"מ לספק שירותים לבקשות הלקוח.
*	שרת הנוד מקבל את הבקשות הללו וממקם אותם בתוך תור , התור הזה נקרא Event Queue.
*	לשרת הנוד יש קומפוננטה שנקראת Event Loop , הקומפוננטה נקראת כך מאחר והיא משתמשת בלולאה אינסופית על מנת לקבל בקשות ולעבד אותם .
*	כאמור הEvent Loop  משתמשת בתהליכון יחיד .
*	הEvent Loop בודק האם יש בקשות בתור , אם לא הוא ימשיך להמתין לבקשות באופן אינסופי.
*	אם כן אזי הוא בוחר את אחד מהם מהתור ואז : 
<br>  

* תתחיל לעבד את בקשת הלקוח.
*	אם הבקשה הזו לא דורשת שום פעולת I.O אזי תעבד את כולה תכין response ושלח אותו בחזרה ללקוח.
*	אם הבקשה דורשת פעולת I.O כמו תקשורת עם הדאטה בייס , שימוש בFile System , שירותים חיצוניים ,  אזי היא בפועלת בדרך שונה :
<br>  

*	תבדוק את זמינות התהליכונים בThread Pool . 
*	תבחר תהליכון אחד ותקצה את הבקשה לתהליכון זה.
*	התהליכון הזה אחראי לקחת את הבקשה , לעבד אותה , לבצע את פעולות הIO , להכין Response ולשלוח אותה בחזרה לEvent Loop.

## ש. מה זה npm בNode.js ? 

ת. NPM הוא ראשי תיבות של Node Pacakge Manager. הוא מספק שני פונקציוניות עיקריות:

* הוא משמש כמאגר אינטרנטי עבור חבילות/מודולים עבור Node.js שאפשר למצוא ב <nodejs.org>
* הוא משמש כCLI על מנת להתתקין חבילות , לנהל גרסאות ותלויות של חבילות של נוד.

ניתן לבדוק את הגרסה של npm כך :


```js

npm --version

```

על מנת להתקין חבילה נשתמש בפקודה הבאה :

```js

npm install <Module Name>


```


## ש. למה נבחר המונע V8 של גוגל ?

ת. מנוע זה פותח ע"י גוגל , הוא אופן סורס והוא כתוב ב C++ כך שיש לו ביצועים טובים.
הV8 נועד לשפר את מהירות הביצוע של Javascript בדפדפני אינטרנט. במקום להשתמש במפרש (interpeter) , V8 ממיר את קוד הJS לקוד מכונה יעיל יותר מה שגורם לשיפור הביצועים.
 
## ש. כמה סוגי פונקציות API יש בNode.JS?

ישנם שני סוגים : 

* פונקציות אסינכרוניות , לא חוסמות - בדר"כ פעולות I.O שניתן להסיט מהmain loop .
* פונקציות סינכרוניות וחוסמות

## ש.למה Node.JS היא single-threaded ? 

ת.Node.JS היא single-threaded כדי לבצע עיבוד אסינכרוני . באמצעות עיבוד אסינכרוני על תהליכון יחיד תחת עומס אינטרנטי טיפוסי ניתן להשיג ביצועים טובים יותר מאשר בעיבוד מבוסס תהליכים טיפוסי(Thread-Based)

## ש. הסבר מה היא פונקציית callback ב Node.JS ?

ת. זוהי פונקציה שנקראת לאחר ביצוע משימה מסויימת , היא מאפשרת לקוד אחר לרוץ במקביל והיא מונעת חסימה. בהיותה פלטפורמה אסינכרונית נוד מסתמכת מאוד על פונקציות Callback . כל הAPIs של נוד נתמכות ע"י פונקציות Callbacks

## ש. הסבר מהו Promise ? 

ת.Promise מייצג השלמה ( Completion ) או כשלון של פעולה אסינכרונית ואת הערך המתקבל ממנה.

לPromise יש שלושה מצבים :

* ממתין (pending) - זהו המצב ההתחלתי , הפרומיס לא קוים (fulfilled) ולא נדחה (rejected)
* קוים (fulfilled) -  משמעותו שהפעולה התבצעה בהצלחה
* נדחה (rejected) -  משמעותו שהפעולה נכשלה.

נראה דוגמה פשוטה : 


```js
var promise = new Promise(function(resolve, reject) {
  const x = "nodejsinterviewquestions";
  const y = "nodejsinterviewquestions"
  if(x === y) {
    resolve();
  } else {
    reject();
  }
});
   
promise.
    then(function () {
        console.log('Success');
    }).
    catch(function () {
        console.log('Some error has occurred');
    });


```
1.Promises משמשים לטיפול אסניכרוני בevents.
<br>
2.Promises משמשים לטיפול בבקשות Http אסינכרוניות


## ש. מהו Callback Hell ?

ת. מספר Callbacks מקוננים אחד מתחת לשני אשר יוצרים צורה של פירמידה , כל Callback תלוי/מחכה לCallback הקודם מה שגורם ליצרת פירמידה  כאמור, דבר המקשה על קריאות הקוד והיכולת לתחזק אותו.


## ש. מה היתרון של Promise על Callback ? 

ת.Promise יכול להתמודד עם מספר פעולות אסינכרוניות בקלות , כמו כן הוא מספק טיפול טוב יותר בשגיאות (error handling). בשימוש בPromise אנחנו בעצם נמנעים מהCallback Hell.

## ש. הסבר את הרעיון של Middleware ? 

ת. זוהי פונקציה שמקבלת את האובייקים של  הבקשה (request) ושל התגובה (response) . מרבית המשימות שMiddleware מבצע הם :

* ביצוע קטע קוד
* לעדכן או לשנות את אובייקטי הבקשה והתגובה
* לסיים את מחזור הבקשה-תגובה.
* להפעיל  את ה Middleware הבא במחסנית.
<br>

![image](https://user-images.githubusercontent.com/37695804/200764854-b43fa365-a407-4113-a29f-6b1f3745a3e9.png)

## ש.מהו Express.js ולמה שנשתמש בו ?

ת. Express.js הוא פריימוורק לנוד שמספק פיצ׳רים נרחבים לבניית לאפליקציות ווב ומובייל . הוא משמש לבניית single page, multipage ו hybrid web application.

הפיצ׳רים של Express.js :

* **פיתוח מהיר יותר של צד השרת** - Express מספקת פיצ׳רים שמישים רבים של Node.js בצורת פונקציות מוכנות שניתן להתשמש בהן בתכנית מה שגורם לחסכון בזמן , שכן אין צורך לכתוב את הפונקציות הללו בעצמנו.
* **הMiddleware** - הMiddleware הוא חלק בתכנית שיש לו גישה לדאטהבייס , לבקשת הלקוח (client req) ולmiddlewares אחרים.הוא אחראי בעיקר על הארגון המערכתי של פונקציות שונות באקספרס.

* **ניתוב (Routing)** - מתייחס לאופן שבו כתובות האתרים של נקודת הקצה של אפליקציה מגיבות לבקשות לקוח 

* **תבניות (Templating)** - אקספרס מספקת מנועי תבנית שמאפשרים למפתחים לבנות תוכן דינמי בדפי האינטרנט ע״י בניית תבניות HTML בצד השרת.
* **דיאבגינג (Debugging)** - דיבאגינג הוא קריטי לפיתוח מוצלח של אפליקציות ווב. אקספרס הופכת את הדיבאגינג לקל יותר ע״י כך שהיא מספקת מנגון בעל יכולת לאתר במדויק את החלק של האפליקציה שיש בו באגים.


## ש. מהם סוגי בקשות הHTTP השונות ?

ת. HTTP מגדיר קבוצה של מטודות בקשה המשמשות לביצוע פעולות רצויות. מטודות הבקשה כוללות:

* GET - משמש לאחזור נתונים
* POST - מבקש מוובסרבר לקבל את הנתונים שנשלחים אליו ע"י המטודה , בדר"כ על מנת לאחסן את הנתונים.
* HEAD - דומה לGET אבל מבקש את התגובה ללא הBODY.
* DELETE - משמש למחיקת המשאב/נתונים מוגדרים
* PUT - משמש לשינוי משאב קיים.

## ש. מה הוא ה Event Loop בNode.JS ?

ת. הEvent Loop אחראי בעצם על טיפול בCallbacks האסינכרוניים , זהו היסוד של פעולות I.O שאינן חוסמות , לפיכך זהו אחד המרכיבים החשובים ביותר בNode.js.


## ש. מהו error-first callback ב Node.js ?

פונקציה שהארגומנט הראשון שלה הוא אוייבקט השגיאה , אובייקט זה מוחזר כאשר מתרחשת שגיאה בעת ביצוע הפונקציה , והארגומנט השני שלה הוא הדאטה שתוחזר במידה ולא מתרחשת שגיאה , במצב זה אוייבקט השגיאה מאותחל לNULL.

בדוגמה הבאה נקבל שגיאה : 
```js

// נשתמש במודול הfs 
const fs = require("fs");

// הקובץ לא קיים במערכת
const file = "file.txt";

// אמור להיזרק שגיאה
// באמצעות הerror first callback
const ErrorFirstCallback = (err, data) => {
if (err) {
	return console.log("Error: " + err);
}
console.log("Function successfully executed");
};

// ביצוע הפונקציה
fs.readFile(file, ErrorFirstCallback);

```
בדוגמה הבאה הצלחה : 
```js


// נשתמש במודול הfs
const fs = require("fs");

const file = "file.txt";

// נקרא לפונקציה כדי לקרוא את הקובץ
// עם קולבק של שגיאה ונתונים
const ErrorFirstCallback = (err, data) => {
if (err) {
	return console.log(err);
}
console.log("Function successfully executed");
console.log("File Content : " + data.toString());
};

// ביצוע הפונקציה
fs.readFile(file, ErrorFirstCallback);


```

## ש. מהם האובייקטים הגלובליים של Node.js?

ת.
<br>
1.let myvar משתנה גלובלי שמוכרז מחוץ לפונקציה ( או פונקציות  ).
<br>
<br>
2.proccess  - זה משתנה גלובלי מובנה שהוא Instance של הEventEmitter שבאמצעותו נתין לקבל את האינפורמציה על הפרוסס הנוכחי , ניתן לגשרת אליו באמצעות require.
<br>
<br>
3.console – משתנה גלובלי שבאמצעותו נתין לכתוב לstdout וstderr .
<br>
<br>
4.setTimeOut(),cleatTimeOut(),setInterval(),clearInterval() – פונקציות טיימר מובנות.
<br>
<br>
5. __dirname – סטרינג , מציין את שם התיקייה שכרגע מכילה את הקוד.
<br>
<br>
6.__filename – מציין את שם הקובץ של הקוד שכרגע מורץ. הערך הוא הנתיב לקובץ.
<br>
<br>


## ש. מהם מודולי הליבה של Node.js?

<div align="center">

| מודול | תיאור |
| --- | ----------- |
| assert | מספק סט של assertion functions שימושיים לטסטים |
|  console | מספק קונסול דיבאגינג פשוט. |
|  crypto | מספק פונקציונליות קריפטוגרפית |
|  http | מכיל מחלקות שיטות ואירועים כדי ליצור שרת http |
|  url | כולל שיטות לרזולציות ופירסור ( parsing ) עבור URL. |
|  querystring | שיטות לטפל ב query string |
|  path | שיטות להתמודדות עם נתיבי קבצים |
|  fs | מחלקות שיטות ואירועים לעבודה עם file IO |
| util |  כולל פונקציות שירות שימושיות למפתחים |

</div>


## ש.מהו הEvent Emitter ? 
הEventEmitter הוא מחלקה שמקלה על אינטרקציה/תקשורת בין אובייקטים ב NODE.JS , המחלקה יכולה לשמש כדי ליצור ולטפל באירועים מותאמים אישית.
הEventEmitter  הוא הליבה של הארכיטקטורה האסינכרונית מוכוונת אירועים של NODE . רבים מהמודולים המובנים של NODE יורשים ממנו כולל ספריות בולטות כמו Express. לאובייקט Emitter יש שני פי'צרים עיקריים :
* "פולט (Emitting) – שמות של אירועים .
* רישום וביטול רישם של listening functions.

```js


/**
 * Callback Events with Parameters
 */
const events = require('events');
const eventEmitter = new events.EventEmitter();

function listener(code, msg) {
   console.log(`status ${code} and ${msg}`);
}

eventEmitter.on('status', listener); // Register listener
eventEmitter.emit('status', 200, 'ok');

// Output
status 200 and ok


```


## ש. מהן שיטות הEventEmitter הקיימות בNode.js ?

<div align="center">

| שיטה | תיאור |
| --- | ----------- |
| .addListener(event,listener) | מוסיף listener לסוף המערך של הlisteners עבור האירוע המסויים |
|  .on(event,listener) | משמש להוספת פונקציית Callback שתבוצע בעת הפעלת האירוע |
|  .once(event, listener) | הlistener מופעל רק בפעם הבאה שהאירוע מופעל ולאחר מכן הוא נמחק |
| .removeListener(event, listener) | הסרת הlistener ממערך הListeners עבור האירוע המסויים |
|  .removeAllListeners([event])	 | מסיר את כל הlisteners או את אלה המצויינים  |
|  .setMaxListeners(n)	 | באופן דיפולטיבי הEventEmitters ידפיסו שגיאה עבור יותר מ10 listeners עבור אירוע מסויים |
|  .getMaxListeners() | מחזיר את הערך המקסימלי הנוכחי של הemitter שנקבע ע"י emitter.setMaxListeners(n) או את הערך הדיפולטיבי |
|  .listeners(event)	 | מחזיר עותק של מערך הlisteners עבור אירוע מסויים |
| .emit(eventName[, arg1][, arg2][, ...]) |  קורא באופן סינכרוני לכל הlisteners שרושמים לeventName בסדר שבו הם נרשמו ומעביר להם את הארגומנטים המסופקים |
| .listenerCount(type)	 |  מחזיר את מספר הlisteners שמאזינים לסוג האירועץ |

</div>


## ש. מהם מטודות התזמון (timing features) של Node.js ?

ת.

* **setTimeout/clearTimeout** - התכונה הזו משמשת כדי לייצר דיליי בביצוע קוד 

* **setInterval/clearInterval** - תכונה זו משמשת לביצוע בלוק של קוד מספר פעמים באפליקציה ( אינטרוול )

* **setImmediate/clearImmediate** - תכונה זו משמשת לביצוע קוד בסוף המחזור של הEvent loop .

* **nextTick** - תכונה זו משמשת לביצוע הקוד בתחילת המחזור הבא של הEventloop.




## ש. הסבר מה זה fork ב Node.js ? 

בעקרון , fork משמש על מנת ״להשריץ״ תהליכים , ב Node.js הfork יוצר מופע נוסף של מנוע הV8 על מנת להריץ מספר workers לביצוע הקוד.


## ש. האם ניתן לגשת ל DOM בנוד ?

ת. לא , אין אפשרות לגשת לDOM.


##  ש. מה זה הREPL בNode.js ? 

ת. REPL ראשי תיבות של Read , Eval , Print , Loop. זוהי סביבה כמו הwindows console או הLinux Shell שבה המשתמש מכניס פקודה , והקונסול מגיב בפלט.

<div align="center">
	
![image](https://user-images.githubusercontent.com/37695804/200756749-1326ad8d-9074-4713-ac8e-9919a02e3258.png)
	
</div>

## ש. מהם Streams בNode.js ? 

הStreams הם אובייקטים שמאפשרים לקרוא נתונים ממקור כלשהו ולכתוב נתונים ליעד כלשהו. יש ארבעה סוגי Streamsבנוד :

* **Readable** - נועד כדי לקרוא אופרציותֿ
* **Writeable** - נועד כדי לכתוב אופרציות.
* **Duplex** - משמש גם לקריאה וגם לכתיבה של אופרציותֿ.
* **Transform** - סוג של Duplex  , כאשר הפלט מחושב לפי הקלט.

קריאה מStream :
```js
const fs = require("fs");
const data = '';

//a. צור סטרים קריא
const readerStream = fs.createReadStream('input.txt');

// b.קבע את הקידוד להיות utf8 
readerStream.setEncoding('UTF8');

// c. טפל באירועים -> נתונים , סיום ושגיאות
readerStream.on('data', function(chunk) {
   data += chunk;
});

readerStream.on('end',function() {
   console.log(data);
});

readerStream.on('error', function(err) {
   console.log(err.stack);
});

console.log("Program Ended");

```

כתיבה לStream :
```js
const fs = require("fs");
const data = 'Simply Easy Learning';

// a. צור סטרים כתיב(writeable)
const writerStream = fs.createWriteStream('output.txt');

// b. כתוב את הנתונים בקידוד utf8
writerStream.write(data,'UTF8');

// c. סמן את סוף הקובץ
writerStream.end();

// Handle stream events --> finish, and error
writerStream.on('finish', function() {
   console.log("Write completed.");
});

writerStream.on('error', function(err) {
   console.log(err.stack);
});

console.log("Program Ended");



```
הצנרה ( Piping ) של Streams :


```js

const fs = require("fs");

// a. צור סטרים קריא
const readerStream = fs.createReadStream('input.txt');

// b. צור סטרים כתיב
const writerStream = fs.createWriteStream('output.txt');

// c. הצנר את פעולות הקריאה והכתיבה
// d. קראת את input.txt וכתוב ל outout.txt
readerStream.pipe(writerStream);

console.log("Program Ended");


```


## ש. הסבר את הקונספט של מודול הURL בNode.js ? 

ת. מודול הURL בנוד מפצל כתובת למספר חלקים קריאים. על מנת לכלול את המודול יש להשתמש בrequire . על מנת לנתח את הכתובת יש להמתמש במטודה url.parse() , מתודה זו תחזיר אובייקט URL שהתכונות שלו הם כל חלק מכתובת. דוגמה :

```js

/**
 * URL Module in Node.js
 */
const url = require('url');
const adr = 'http://localhost:8080/default.htm?year=2022&month=september';
const q = url.parse(adr, true);

console.log(q.host); // localhost:8080
console.log(q.pathname); // "/default.htm"
console.log(q.search); // "?year=2022&month=september"

const qdata = q.query; // { year: 2022, month: 'september' }
console.log(qdata.month); // "september"


```
