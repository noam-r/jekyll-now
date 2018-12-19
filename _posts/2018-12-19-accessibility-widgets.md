---
layout: post_page
title: תוספי נגישות מסוכנים - פרק ראשון בפודקאסט החדש סייבר סייבר
description: 
---

באוקטובר 2017 פורסם תיקון לתקנות העוסקות בנגישות האינטרנט, וקבע שורה של כללים שנועדו להקל על בעלי מוגבלויות לגשת לתכנים המפורסמים ברשת. התקן הישראלי הוא בעצם אימוץ של הנחיות בינלאומיות - Web Content Accessibility Guidelines של ארגון ה W3C הבינלאומי ומקלות על אנשים עם מוגבלויות שונות כגון עיוורים ומוגבלי ראיה, אנשים עם מוגבלות פיזית המתקשים להפעיל את ידיהם, אנשים עם מוגבלויות קוגניטיביות כגון דיסלקסיה והפרעות קשב וריכוז, אנשים עם מוגבלות שמיעה' ואנשים עם מוגבלויות אחרות.

למשל: משתמשת עיוורת העושה שימוש בתוכנה המקריאה את התכנים בעמוד תוכל לקרוא את כל הטקסטים בסדר הגיוני, לקבל תיאור של מידע המצוי בתמונות, לזהות כותרות וקישורים ולהיות מסוגלת להפעיל את כל מה שיש באתר כגון קישורים, טפסים, כפתורים. בלי התקן הזה המשתמשת עשויה לקבל קודם את התפריט התחתון, אחר כך את הפרסומות, ובסוף, אולי, גם את התכנים שלמענם הגיעה לעמוד מלכתחילה.

או משתמשת שמטעמים שונים לא יכולה או לא מצליחה להפעיל עכבר. התקן מאפשר ניווט באמצעות מקלדת והגעה לכל השדות והכפתורים הנדרשים.

או משתמשת שאינה שומעת כראוי יכולה לסמוך על כך שיהיו כתוביות בסרטונים או בקטעי השמע המופצים באתר. ועוד כיוצא באלה.

{:refdef: style="text-align: center;"}
![accessibility](/img/2018-12-19-00.jpg)
{: refdef}

עד כאן - נשמע מעולה. אוכלוסיה מוחלשת המקבלת מענה מהמדינה שיעזור לה לנווט ברשת הישראלית, והגזר הזה אפילו מגיע עם מקל - גוף שלא ינגיש את המידע שלו יוטלו עליו קנסות ועונשים אחרים. כמובן שיש שלל סייגים לגבי המחזור הכספי של הגופים שחייבים בהנגשה, אבל עדיין - התערבות של המדינה בשוק החופשי למען אוכלוסיה שפעמים רבות נוטים להתעלם ממנה. שאפו.

אבל אם אתם מתארים לעצמכם שלא היינו מדברים על זה אם כאן היה נגמר הסיפור - תנו לעצמכם ביסקוויט, אתם צודקים לחלוטין.

**הדרך לגיהנום רצופה בכוונות טובות**

על מנת להתאים את העמוד והתכנים לעמוד בהוראות החוק, על בעלי האתרים (הפאבלישרים) לעשות מספר שינויים בתבנית העמודים ובתכנים עצמם, כמו למשל להגדיר כותרות לטבלאות (בעזרת אלמנט TH), לשים תוויות ALT על תמונות, לשים תוויות (Labels) על כל שדה, ועוד ועוד, לא ניכנס לזה עכשיו למרות שזה יכול להיות מעניין להזדמנות אחרת, וגם להוסיף "תוסף" (או ביידיש: ווידג'ט) שיטען עם העמוד ויאפשר שורה של פעולות אקטיביות כמו שינוי גודל גופן, שינוי ניגודיות הצבעים, וכיוצא באלה.

החלק הראשון - זו ממילא שיטת עבודה נכונה, כך צריך לבנות עמוד, ומי שלא עושה את זה מראש כדאי שיתיישר עם הסטנדרטים המקובלים ולא יעגל פינות. עם זה אין בעיה. הסיפור שלנו מתחיל עם התוסף האקטיבי, זה שנטען עם העמוד, ולצורך הבנה של הבעייתיות בסיפור הזה בואו ניקח חברה דימיונית בשם "עמי בורקס" שמפעילה שירות משלוחי פחמימות ברחבי הארץ, ונדרשת להתאים את המערכת שלה לדרישות החוק.

**במרתפי הפיתוח של עמי בורקס**

ובכן, מחלקת הפיתוח של עמי בורקס עסוקה מאוד בהעלאה של פיצ'ר חדש שיאפשר לגולשים בחור דוגמה בה יפוזר השומשום על המאפה לפני הכנסתו לתנור כך שהמשתמשים יוכלו לשלוח זה לזה מסרים רומנטיים, כי כידוע שום דבר לא אומר "אני אוהב אותך" כמו סמבוסק מעוצב אישית. מנהל הפיתוח, למרות הרצון הטוב שלו, לא רואה את עצמו מוצא את הזמן להתחיל לקרוא את עשרות עמודי התקן, להבין אותם, לאפיין תוסף שיענה על כולם, ואז להקדיש מפתח שישב על זה במשך מספר שבועות, לקחת משאבים ממחלקת ה-QA, וזאת בשעה שעתיד החברה עומד על הכף. אם הוא לא יצליח לשחרר את הפיצ'ר החדש בזמן - יעשו קיצוצים כואבים במחלקה שלו שיהפכו את פיתוח התוסף למשימה קשה הרבה יותר.

מנהל הפיתוח התלונן ערב אחד באוזני בן דודו, שגם הוא עובד בתחום, ובן הדוד אמר: "אין סיכוי שכל חברה צריכה לפתח את זה מאפס. בטוח יש כמה יזמים זריזים שעשו את זה בשבילך, והם יתנו לך את הפיתוח שלהם תמורת כמה שקלים". עיניו של מנהל הפיתוח נפקחו בשמחה, הוא אץ ורץ לגוגל והקיש "תוסף נגישות לאתרים", ומצא שלל פתרונות מוכנים. "ניצלתי", הוא לחש בליבו, בחר את אחד מהפתרונות, ולמחרת בבוקר הורה לעובדים במחלקה שלו להטמיע את הפתרון באתר.

הדרך בה עובדים הפתרונות האלה, בדרך כלל, היא פשוטה מאוד ודורשת מהאתרים להטמיע חתיכת קוד על כל העמודים שלהם, מה שהם ממילא עושים עם פתרונות דומים כמו קוד הניטור של גוגל אנליטיקס, או הכפתורים של פייסבוק. זה רק עוד קוד שנטען משרת חיצוני. לא נדרש מהאתר לארח שום דבר אצלו, רק לעשות קופי & פייסט. כשנטען העמוד של עמי בורקס, הקוד שהודבק בו פונה לשרתי חברת תוסף הנגישות, טוען קוד נוסף, ומצייר את התוסף על העמוד. חיים טובים וקלים. האתרים לא צריכים להמציא את הגלגל כל פעם, וחברת התוספים (בתקווה) יודעת מה שהיא עושה מבחינת דרישות החוק. כולם מרוויחים, ובעיקר הגולשים שצריכים את התוסף לצורך נגישות לתכנים.

**פרצה קוראת לגנב**

וכאן נכנסים לתמונה גורמים מרושעים יותר.

דמיינו לעצמכם שיכולתם להזריק איזה קוד שאתם רוצים לשורה ארוכה של מערכות על ידי פגיעה במערכת אחת בלבד. דמיינו לעצמכם שהייתם יכולים לשתול קוד ששולח לכם כל הקשה על מקלדת בשדות מסוימים, נניח שם משתמש וסיסמה, או לשלוח לצד שלישי פרטים מסוימים בעמוד כמו מצב החשבון או מספר כרטיס האשראי שמקישים המשתמשים בדף התשלום. 

בריטיש איירוויז, למשל, נפלה קורבן בדיוק למתקפה כזו. האקר מרושע שתל קוד קטן בדף התשלום ששלח לו את כל מספרי כרטיסי האשראי שהוקשו בו, והם לא היחידים. למצוא מתקפה כזו זה עניין לא קל, ובדרך כלל לוקח שבועות, ולפעמים חודשים, עד שעולים על זה שיש איזו בעיה, בדרך כלל אחרי שמוצאים את פרטי כרטיסי האשראי למכירה ברשת האפלה או בפורומים יעודיים, ואז כבר ממש מאוחר מדי. 

וזה בדיוק מה שמאפשרת הטמעת התוסף הזה באתרים הישראלים.

תגידו - אבל קודם אמרת שממילא מטמיעים קוד חיצוני מגוגל ומפייסבוק! ואתם כמובן צודקים, אבל לכו תשוו את האבטחה של גוגל ושל פייסבוק לזו של חברה ישראלית ממוצעת. אתם לא באמת צריכים לעשות את זה - אני כבר עשיתי את זה בשבילכם.

**אבטחה זה שם של דג**

הלכתי ובדקתי כמה תוספים כאלה שהקוד שלהם נטען על ידי כמה גופים גדולים ומכובדים כמו משרדי ממשלה למשל, או קמעונאים גדולים, או חברות תקשורת, או ארגונים שמחזיקים מידע רפואי רגיש, ולא תתפלאו שמצאתי שורה ארוכה מאוד של כשלים שבמקרה אחד איפשרו הזרקה של קוד זדוני שהיה נטען אצל כל אחד מלקוחותיהם, שכאמור חלקם היו גדולים ומכובדים.

רבים מהשירותים האלה יושבים על שרת משותף עם אבטחה מזעזעת שבאמת לא נדרש יותר מדי כדי להיכנס אליו. באחד מהשירותים שבדקתי אפילו זה לא היה נחוץ. הממשק שלהם פשוט היה פתוח לחלוטין ואיפשר הזרקה של קוד. הם פשוט לא בדקו מה שולחים להם ואם שם המשתמש, למשל, הוא לא פקודה מרושעת. (והוא היה).

שירות אחר, ככל הנראה, לא שמע כלל על אבטחת מידע וקיומם של גורמים פחות נחמדים, והשאיר את מערכת הקבצים שלו נגישה לגמרי כך שאפשר היה להעלות ולשנות קבצים, שכזכור נטענו על ידי שלל אתרים אחרים. היה כל כך קל להשתיל שם רושעה שפוטנציאל הנזק שלה היה משמעותי מאוד.

**בוטנים, קופים, וכיוב**

חלק מהשירותים האלה עולים כמה שקלים, חלקם חינמיים, אבל כמו שאומר הפתגם הידוע: מי שמשלם בבוטנים - מקבל קופים. הבעיה כאן היא אחרת: מנהלי אבטחת מידע משקיעים תועפות של כסף במערכת שלהם. ציוד, בדיקות, הגנות, הכל, אבל אז מכניסים פנימה קוד מפוקפק שנטען ממקור מפוקפק עוד יותר.

זה דומה לארגון שמתקין אמצעי אבטחה חמורים בכניסה, אבל אז מכניס פנימה היפי שמזמין את כל החברים המפוקפקים שלו ושולח להם את כל המידע שעליו יש להגן.

אבל זה לא כל מה שמצאתי.

אחד מהשירותים האלה, דווקא כזה שהותקן במערכת של משרד ממשלתי גדול, החליט לדחוף פנימה פרסומת לשירות פרטי לחלוטין המציע עזרה בהחזר מיסים. האם הקוד הזה עבר בדיקה על ידי גורם אחראי? כמובן שלא, אחרת לא היה עולה לסביבת הייצור. האם המערכת החיצונית הזו עברה בדיקת אבטחה של גוף רציני? כמובן שלא, אחרת לא היה לוקח בדיוק ארבע דקות להשתלט עליה.

אז איך זה קורה? בשתי מילים: חוסר מודעות. שום מנהל אבטחה שמכבד את עצמו לא היה מאפשר התקנה של תוסף חיצוני של חברה קיקיונית בלי שבדק בעצמו את האבטחה בה, והרציניים מביניהם גם היו דורשים לעבור על הקוד בעצמם, ולדאוג שהקוד יטען תוך בדיקה שמדובר באותו הקוד.

יסלחו לי האנשים הפחות טכניים, אבל בדיוק בשביל זה קיים מה שנקרא Subresource Integrity (SRI), שמאפשר לטעון סקריפטים (או כל דבר אחר) תוך בדיקת ה"האש" שלהם, קרי, שהקובץ הנטען הוא בדיוק בדיוק זה שנבדק על ידי המערכת שהטמיעה אותו. הפיצ'ר הזה נתמך על ידי כל הדפדפנים המודרניים, ובעצם אין תירוץ לא להשתמש בו.

בנוסף, וזה מהלך שעשו כל הבנקים הישראלים בחודשים האחרונים, כי הם באמת מנסים לקחת את האבטחה שלהם ברצינות, זה פשוט לא להשתמש בתוספים חיצוניים. חלקם עדיין משתמשים בתוסף שפותח על ידי צד שלישי, אבל הוא נטען מהמערכות שלהם ולא מאתר חיצוני. כך הם יכולים לוודא שהסקריפטים הנטענים לא שונו בלא ידיעתם.

**בעולם קצת יותר טוב**

תקנות הנגישות הן טובות וחשובות, והדברים המובאים כאן לא נועדו לדכא את בעלי האתרים מלעמוד בהן. הבעיה, כרגיל, היא קיומן של חברות קיקיוניות שמנסות לעשות קופה על חשבון הסיפור הזה. מה שצריך לעשות, בעיני, זה לפתח תוסף כזה בקוד פתוח שיהיה גמיש מספיק מצד אחד, ונוח מספיק לשימוש מהצד השני, כדי שכל בעל אתר יוכל לקחת אותו אליו בחינם ולהתקין אותו בקלות.

בעולם קצת טוב יותר זה היה צריך להיות פרויקט ממשלתי שהיה יוצא לפני כניסתן לתוקף של תקנות הנגישות, אבל מכיוון שזה לא קרה, טוב יהיה אם קבוצה של מפתחים בעלי אחריות חברתית יקחו את זה על עצמם. זה באמת לא צריך להיות מורכב מדי, והיתרונות שפרויקט כזה יכול להביא הם עצומים הן מבחינת הנגישות, והן מבחינת אבטחת המידע שלא תצטרך להסתמך על חובבנותן של חברות קטנות וקיקיוניות.

---

הפוסט הזה הופיע בפרק הראשון בפודקאסט החדש שלי ושל עידו קינן ששמו "סייבר סייבר". לינק להאזנה אפשר למצוא [כאן](https://www.podbean.com/media/share/pb-vu73d-a23292), והסאונד המעולה באחריות [עומר סנש](http://omer.16mb.com/) מ[Podcasti.co](https://www.podcasti.co/). בקרוב נקליט פרקים נוספים בהם נמשיך לדבר על מאפים ופרצות אבטחה, מקווים שתצטרפו אלינו, אבל גם אם לא - אנחנו, לפחות, נהנים מזה.

