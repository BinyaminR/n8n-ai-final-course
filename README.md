# משימת סיום קורס AI + n8n

סטודנט: בנימין רותנברג  
נושא משימה 1: גן החיות התנ"כי בירושלים

## מה יש בריפו

- `workflows/task1-chatbot-biblical-zoo.json` — וורקפלואו הצ'אט
- `workflows/task2-birthday-greeting.json` — וורקפלואו ברכת יום ההולדת
- `knowledge/gan-ha-hayot-tanachi.txt` — קובץ הידע של הגן (פחות מ-5000 מילים)
- `chat/index.html` + `chat/style.css` + `chat/script.js` — הצ'אט המוטמע, החלק העליון כתום

## משימה 1

1. לייבא את JSON ל-n8n.
2. לחבר Credential של Google Gemini.
3. המודל: `models/gemini-1.5-flash`.
4. הזיכרון מוגדר ל-15 הודעות אחרונות.
5. כלי HTTP קורא את הקובץ:
   `https://raw.githubusercontent.com/BinyaminR/n8n-ai-final-course/main/knowledge/gan-ha-hayot-tanachi.txt`
6. להפעיל את הוורקפלואו.
7. להעתיק את כתובת ה-Chat webhook לקובץ `chat/script.js` במקום `PASTE_N8N_CHAT_WEBHOOK_URL_HERE`.
8. לפתוח את `chat/index.html` בדפדפן.

הפרומפט בעברית מגביל את הסוכן לגן החיות התנ"כי בלבד. על מתחרה או נושא אחר הוא אמור לסרב בנימוס.

## משימה 2

1. לייבא את JSON ל-n8n.
2. ליצור ב-Airtable טבלה עם 6 שדות (מלבד ID):
   - שם מקבל הברכה
   - שם מייצר הברכה
   - מין מקבל הברכה
   - תיאור נושאים אהובים
   - ברכה שנוצרה
   - מייל מקבל הברכה
3. להחליף ב-Airtable Node את ה-Base ID ואת ה-Table ID.
4. לחבר Gemini, Airtable ו-Brevo.
5. ב-Brevo להחליף את כתובת השולח לכתובת מאושרת בחשבון.
6. להפעיל את הוורקפלואו ולשלוח POST ל-webhook.

גוף לבדיקה ב-Postman:

```json
{
  "recipientName": "נועה",
  "senderName": "בנימין",
  "gender": "נקבה",
  "favoriteTopics": "סוסים, ציור ושוקולד",
  "recipientEmail": "test@example.com"
}
```

ה-Response אמור להכיל:

```json
{
  "ok": true,
  "message": "הברכה נוצרה ונשלחת ברגעים אלה...",
  "greeting": "טקסט הברכה שה-AI יצר"
}
```
