# Deduplication
import pandas as pd
import nltk

train = pd.read_csv('Train.csv')
#print (train.shape)
train.head()

df1 = train.groupby([train.ln,train.fn,train.dob,train.gn]).head(1) #taking only 1 values of the repeated datas

from nltk.tokenize import word_tokenize
l = []
for w1 in df1.ln:
    l.append(word_tokenize(w1)) # separating words and appending to the list l
df1["surname_total"] = l
#print(df1)

l2 = []
for i in l:
    l2.append(max(i,key=len)) # taking the longest string as surname and appending to list l2 
df1["surname_original"] = l2 # adding this list to a column
#print(df1)

l3 = []
l4 = []
for j in df1.fn:
    l3.append(word_tokenize(j)) #separating words and appending to the list l3
for k in l3:
    l4.append(max(k,key = len)) #taking the longest string as surname and appending to list l4
df1["fn_original"] = l4 # adding this list to a column
#print(df1)

df2 = df1.groupby(["surname_original","fn_original","gn","dob"]).head(1) #grouping by filtered surname_original and fn_original
#df2.drop(["ln"], axis = 1,inplace = True)
#print(df2,df2.shape)

df2[["dob","gn","fn","fn_original","ln","surname_original"]].to_csv("filtered_name.csv",index = False) # created a csv file
pd.read_csv("filtered_name.csv").shape
