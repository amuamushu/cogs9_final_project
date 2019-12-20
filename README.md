# COGS 9 Final Project: Yearly UCSD Application Rate and League Table Linear Regression Model
Authors: Abigail Han, Thanh Luong, Amy Nguyen, Saroop Samra

This project was done for COGS 9: Introduction to Data Science and aims to answer a question revolving UCSD's enrollment rate: whether there was correlation betweeen media influence, as determined by positive/negative sentiment from news articles on UCSD and the school's US World News ranking, and the number of students enrolling every year.

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
     - I extracted the HTML code from the URL using the **Request package**
     - I used certifi to get the root certificates for the webpages and bypass vertification
     - **BeautifulSoup** was used to parse the HTML code and extract only the paragraphs (the article text) from the HTML code

### Data Wrangling
**Twitter CSV:**
  - Used the Panda package to create a dataframe for the data and filter the column containing ithe tweets to only contain meaningful words (words that have a length larger than 3)
**Web Page**
  - filtered the text to only maintain the meaninful words
