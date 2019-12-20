# COGS 9 Final Project: Yearly UCSD Application Rate and League Table Linear Regression Model
Authors: Abigail Han, Thanh Luong, Amy Nguyen, Saroop Samra

This project was done for COGS 9: Introduction to Data Science and aims to answer a question revolving UCSD's enrollment rate: whether there was correlation betweeen media influence, as determined by positive/negative sentiment from news articles on UCSD and the school's US World News ranking, and the number of students enrolling every year.

#### Table of Content

### Project Proposal
The proposal outlines how we are carrying out our project, including the various methods we were intending to use for analysis, and acknowledges the project's ethical considerations.

### Actual Project (The Jupyter Notebook)
Carrying out the actual project was extra credit. Thus, we did not carry out all of the intended methods.

The two types of analysis we carried out were:
1. Predictive Analysis: Linear Regression (done by Saroop)
2. Text Analysis: Sentiment Analysis (done by Amy)

## Sentiment Analysis
### Data Collection
I had two data sources:
1. Twitter Tweet Sentiment CSV
   - Dataset has 2 variables: Emotion (either positive/negative) and Tweet (the content of the message)
   - Used as training data to determine which word is associated most with which sentiment
2. Web page text
   - Each word in the text is used to determine the sentiment of the overall page
   - Used **web-scraping** to get the text from the page
     - I extracted the HTML code from the URL using the **Request library**
     - I used certifi to get the root certificates for the webpages and bypass vertification
     - **BeautifulSoup** was used to parse the HTML code and extract only the paragraphs (the article text) from the HTML code

### Data Wrangling
**Twitter CSV:**
  - Used the Panda package to create a dataframe for the data and filter the column containing ithe tweets to only contain meaningful words (words that have a length larger than 3)
**Web Page**
  - filtered the text to only maintain the meaninful words
  
### Naive Bayes
**Keeping track of emotion of each word in the training dataset**
  - Looped through all of the words in each of the filtered tweets to determine the sentiment frequency of each word based on the overall sentiment of its corresponding tweet. Only the words that occur in the article would have its sentiment frequency counted to ensure that the probability of a word occuring is not 0.
  - Each word has both of its sentiments' frequencies nudged by 1 to prevent the probability of a word occuring being 0 for either of thes sentiments
**Calculating Naive Bayes**
  - Since it is unlikely for a tweet to contain all of the words in the article, we use the Naive Bayes assumption that occurence of each word in the article is independent of each other. Thus, each word would have its own conditional probability to calculate.
### Sentiment Analysis Conclusion
Using the Naive Bayes approach, whichever sentiment has the greater conditional probability is the predicted sentiment for the article

## Overall Issues & Our Solutions
**For Predicitve Analysis**
**For Sentiment Analysis**
1. Getting the HTML code of certain web pages
   - I was getting a URLError for most sites with a message of `[SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:581)`. At first, I did not do anything about it because I thought it just meant that I was not allowed webscrape the site.
   - However, after looking into the error, I solved the issue by discovering the certifi library, a collections of certificates I can use to access webpages. After installing the library, all of the URLs I have tried worked. I also added an except block to create a certificate if there is not one already. [(Source for try-except code)](ttps://incognitjoe.github.io/adding-certs-to-requests.html
2. Parsing HTML Code
   - After using request, we are left with the HTML code, which in all its glory contains lines of identifiers (none of which is meaningful for this analysis).
   - To solve this issue, I scanned the HTML code and noticed a pattern: all of the article text was nested in paragraphs. However, I did not want to just loop through the string of content searching text nested between `<p>` and `</p>` because that way seemed error-prone and space inefficient. I would have to keep track of the text in between as I am looping and constantly add to it. Thus, I decided to use BeautifulSoup to quickly parse the text for only paragraphs.
3. Conditional Probability of 0
   - 

## Overall Technologies Used
**For Predictive Analysis**
**For Sentiment Analysis**
  - Pandas Library
  - PorterStemmer from nltk.stem (for stemming words)
  - Regex
  - BeautifulSoup (for parsing HTML code)
  - Requests Library (for getting webpage content)
  - certifi (for referencing the web page root certificate)
(Amy) Except for Pandas and Regex, this was my first time using these libraries.


Readme written by Amy :)
