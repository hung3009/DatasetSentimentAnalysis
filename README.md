# DatasetSentimentAnalysis
 

 git add .
 git commit -m "viet gi cung duoc"
 git push 


 git pull
 
 hehehe1
 
# CHuyển data IMDB.csv sang Linear Regression bằng code Colab Google Research:

#---------------------------------------------------------------------------------

import pandas as pd

#tải  tập dữ liệu ,chuyển đổi thành các giá trị số tương ứng, ví dụ 1 cho "positive" và 0 cho "negative" của cột sentiment

data = pd.read_csv('https://raw.githubusercontent.com/hung3009/DatasetSentimentAnalysis/main/IMDB_Dataset.csv', encoding='unicode_escape')
data['sentiment'] = data['sentiment'].replace(['positive', 'negative'], [1, 0])


#---------------------------------------------------------------------------------

import re

def clean_text(text):
    text = re.sub(r'[^\w\s]', '', text) #loại bỏ các ký tự đặc biệt như dấu !, ?, ...
    text = text.lower() #chuyển các ký tự thành chữ thường
    return text

data['clean_text'] = data['review'].apply(lambda x: clean_text(x))
print(data.head())

#---------------------------------------------------------------------------------

from sklearn.feature_extraction.text import CountVectorizer

# rút trích đặc trưng từ dữ liệu văn bản
vectorizer = CountVectorizer(stop_words='english')
X = vectorizer.fit_transform(data['clean_text'])

# tập nhãn
y = data['sentiment']

#---------------------------------------------------------------------------------

import matplotlib.pyplot as plt

# tạo dự đoán với dữ liệu kiểm tra
y_pred = lr.predict(X_test)

# vẽ biểu đồ
plt.scatter(y_test, y_pred)
plt.xlabel('Actual')
plt.ylabel('Predicted')
plt.show()

#---------------------------------------------------------------------------------


 
