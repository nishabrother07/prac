# prac
only for using practice python
# print(df[1:3])
काम करने का तरीका (Working Mechanism):
यह कोड DataFrame df की index 1 से index 2 (3 से एक कम) तक की सभी रो (rows) को प्रिंट करता है।

ब्रेकडाउन:
👉 df[start:end] का मतलब:

start (शुरुआती इंडेक्स) → शामिल (inclusive) होता है।
end (अंतिम इंडेक्स) → शामिल नहीं (exclusive) होता है।


import pandas as pd

# एक DataFrame बनाते हैं
data = {
    "name": ["Aman", "Bobby", "Chetan", "Divya", "Esha"],
    "age": [25, 30, 22, 27, 29]
}

df = pd.DataFrame(data)



print(df[1:3])


निष्कर्ष (Conclusion):
यह कोड इंडेक्स 1 से शुरू करता है और इंडेक्स 3 से पहले रुक जाता है (यानी इंडेक्स 2 तक डेटा दिखाता है)।

इंडेक्स 0 की row शामिल नहीं होगी।

इंडेक्स 3 की row भी शामिल नहीं होगी।

👉 तो df[1:3] का मतलब है: इंडेक्स 1 और 2 की rows को दिखाओ। ✅

अगर आपको loc और iloc से इंडेक्सिंग करनी हो:
1. iloc से (Integer-Index Based Slicing)

print(df.iloc[1:3])  # यह भी df[1:3] जैसा ही काम करेगा
2. loc से (Label-Based Indexing)


print(df.loc[1:3])  # ध्यान दें: यहाँ 3 भी शामिल होगा

loc[] में end इंडेक्स भी शामिल होता है, जबकि df[start:end] और iloc[] में नहीं होता।

अगर आपको कोई और डाउट हो तो बताइए! 😊



1️⃣ drop() का उपयोग कॉलम हटाने के लिए (axis=1 के साथ)

df.drop("column_name", axis=1, inplace=True)
उदाहरण:
df.drop("humidity", axis=1, inplace=True)  # 'humidity' कॉलम हटाएगा

2️⃣ del का उपयोग कॉलम हटाने के लिए
del df["column_name"]



del df["humidity"]  # 'humidity' कॉलम हटा देगा

👉 axis=1 क्यों दिया जाता है?
axis=0 → रो (row) हटाने के लिए
axis=1 → कॉलम (column) हटाने के लिए

📌 निष्कर्ष:
Row हटाने के लिए: df.drop(7, inplace=True)
Column हटाने के लिए:

df.drop("column_name", axis=1, inplace=True)
del df["column_name"]








Pandas में drop() फंक्शन का सिंटैक्स (Syntax)
 
df.drop(labels, axis, inplace, errors)

📌 पैरामीटर्स की व्याख्या (Explanation of Parameters):
पैरामीटर	विवरण
labels	रो (rows) या कॉलम (columns) का नाम या इंडेक्स, जिसे हटाना है। (List भी दी जा सकती है)
axis	0 → Row हटाने के लिए, 1 → Column हटाने के लिए
inplace	True → DataFrame को स्थायी रूप से बदल देता है, False → नई कॉपी लौटाता है
errors	ignore → अगर नाम न मिले तो एरर नहीं देगा, raise (default) → एरर देगा

📝 1️⃣ Row हटाने का Syntax

df.drop(index, axis=0, inplace=True)


df.drop(7, inplace=True)  # Index 7 की row हटाएगा
df.drop([2, 5, 8], inplace=True)  # Index 2, 5 और 8 की rows हटाएगा

📝 2️⃣ Column हटाने का Syntax

df.drop(column_name, axis=1, inplace=True)

df.drop("humidity", axis=1, inplace=True)  # 'humidity' कॉलम हटाएगा

df.drop(["temperature", "pressure"], axis=1, inplace=True)  # 'temperature' और 'pressure' कॉलम हटाएगा

📌 del का उपयोग कॉलम हटाने के लिए (दूसरा तरीका)

del df["column_name"]

del df["humidity"]  # 'humidity' कॉलम हटा देगा

🔹 drop() और del में अंतर

Method	Row हटा सकता है?	Column हटा सकता है?	Permanent (inplace) Option

df.drop()	✅ हाँ	✅ हाँ	✅ हाँ
del df["column"]	❌ नहीं	✅ हाँ	🔴 हमेशा स्थायी (permanent)
