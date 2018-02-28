# Deduplication
In this problem due to less no of data available for unsupervised learning, I have tried a different approach where for grouping of similar "fn" and "ln" I have considered the largest string as the main attribute.

Main libraries used are word_tokenizer for tokenizing the elements and max(str, key) for output of max string in a list of lists. pd.DataFrame.groupby([<arguments_of_columns>]).head(1) as to get one unique value from the repeated datas.

Requirements for running the code:

Python 3.5+

Pandas (in cmd type "pip3 install pandas")

Jupyter Notebook (in cmd type "pip3 install jupyter")

NLTK {

(in cmd type "pip3 install nltk")

(next type python in cmd)

(import nltk

nltk.download)

(download all the requirements, may take from minutes to an hour or two depending on your internet connection)
