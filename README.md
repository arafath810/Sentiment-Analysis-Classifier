# Sentiment-Analysis-Classifier
import pandas as pd
from textblob import TextBlob
import matplotlib.pyplot as plt
# 1. Create a simple dataset (This looks like a lab exercise)
data = {
    'Review':[
        "IBM is a great company to work for!",
        "The project was very difficult and frustrating.",
        "I am learning a lot about data science.",
        "The service was okay, nothing special.",
        "I hated the interface of the new application."
    ]
    }
df=pd.DataFrame(data)
# 2. Human-style logic: Define a function to get sentiment
def get_sentiment(text):
  analysis = TextBlob(text)
   # Using Polarity: > 0 is Positive, < 0 is Negative, 0 is Neutral
  if analysis.sentiment.polarity > 0:
      return 'Positive'
  elif analysis.sentiment.polarity < 0:
      return 'Negative'
  else:
      return 'Neutral'
# 3.Apply the function to our data
print("Processing reviews...")
df['Sentiment'] = df['Review'].apply(get_sentiment)
# 4. Display results
print("\n--- Final Sentiment Results ---")
print(df)
# 5. Simple visualization (Recruiters love a quick chart)
df['Sentiment'].value_counts().plot(kind='bar',color=['green', 'red', 'blue'])
plt.title('Customer Review Sentiments')
plt.xlabel('Category')
plt.ylabel('Number of Reviews')
plt.show()
