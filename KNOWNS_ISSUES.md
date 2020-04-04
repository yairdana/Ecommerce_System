# Ecommerce_System
Final Project for "Object-Oriented Programming in C++" Course.
KNOWNS ISSUES

אבחנות:
1. המערכת אינה בודקת את תקינות הקלט מבחינת טיפוס הנתונים הנקלט.
כלומר, במידה ונקלוט char במקום int לדוגמא בתפריט הראשי. המערכת תיכנס ללולאה אינסופית.

2. המערכת שלנו עושה אבחנה ליקסקוגרפית.
כלומר, המשתמש Alon והמשתמש alon הם שמות משתמשים שונים מבחינת המערכת.

3.  בהצגת "כלל המוצרים ע"פ שם" יוצגו כל המוצרים כולל המוצרים הלא זמינים של המוכרים.

4. ניתן לייצר הזמנות (ריקות גם) ללא הגבלה - כפי שהובן לנו מהוראות התרגיל

5.  USER הוגדרה כמחלקה אבסקטרקטית ע"י השיטה show=0 שכן, כל User  הוא למעשה קונה/מוכר/קונה-מוכר. לא איפשרנו יצירתי אובייקט שהוא יוזר בלבד.

6. במחלקות השונות: יוזר, קונה, מוכר, קונה-מוכר, ביטלנו את הCOPY CTOR שכן לא נרצה לשכפל משתמשים במערכת שלנו.
MOVE בוטל גם הוא מהמחלקות השונות שכן, אין הקצאות דינמיות עבור מערכי VECTOR ושימוש במחלקת STL.

7. במערכת לא איפשרנו לקונה-מוכר (Megauser) לקנות מוצרים השייכים לעצמו.
 
8. במחלקות ORDER, BUIYRER, SELLER המחזיקות מערכים של מצביעים למוצרים/רשימות וכדומה. השיטות לקבלת המערך לדוגמא: getOrderList. ממומשות ב-protected לצורך הורדת הרשאה ושימוש אשר יכול לשנותם. 
לכן אפשרנו רק לחברים ומחלקות יורשות את הגישה אליהם.

הזמנות:
1. בגלל דרישות התרגיל, כאשר 2 מוצרים זהים קיימים ב2 הזמנות שונות, ואחת מההזמנות שולמה, ההזמנה שטרם שולמה, לעולם לא תוכל להתבצע, כי היא מכילה מוצר שכבר אינו זמין (ז"א אינו במלאי)
אם כי קיימת פונקציה במחלקת "הזמנה" שמאפשרת את מחיקת המוצר  שאינו זמין מההזמנה, אך אינה מופיעה בתפריט המבוקש בתרגיל.

2.  לאחר שיצרת הזמנה - אין באפשרותך להוסיף דרך התפריט מוצר נוסף להזמנה ההקיימת, אך ישנן פונקציות כאלה בתוך מחלקת "הזמנה" שמאפשרת הוספת/מחיקת מוצרים.

3. המערכת אינה מעדכנת את המוכר כי המוצר שלו נמכר, 
אם זאת כל מוכר יוכל לגשת לרשימת המוצרים שלו ושם לראות האם המוצר נמכר או לא - מוצרים שנמכרו יקבלו ערך "לא זמין" ובנוסף את כתובת אוביקט ה"קונה" -כך מוכר יוכל לראות למי מכר ולאן לשלוח.
כדי לא לאפשר למוכר לגשת לפרטים סודייים כגון : PASSWORD של קונה מסויים. השיטה  getPassword נבחרה להיות תחת protected