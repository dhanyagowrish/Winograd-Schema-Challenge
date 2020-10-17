# Winograd Schema Challenge  
The model aims to identify the correct antecedent of a specified pronoun in a sentence/schema.   

The **city councilmen** refused the **demonstrators** a permit because *they* feared violence.  

Here, the correct andecedent of the pronoun **they** would be "city councilmen"  

## Datasets  

**WSC-285** contains 285 schemas  

**WinoGender** contains 120 schemas. ( WinoGender is usually used for testing if a model is biased toward gender i.e if the model tends to associate certain professions with certain pronouns. But since our model does not consider pronoun in the feature vector formation, WinoGender is used in training here )  

## Approach  
An SVM based approach was used to indentify the correct antecedent.   

* In every sentence stopwords and punctuation is removed   
  
* The words are POS-tagged  

* In all the words aside from the candidate antecendents, 2 keywords are identified  

* Find similarity for every candidate-antecedent pair using cosine similarity of the word vectors  

* The above 4 features is the feature vector for the sentence  

### Keyword identification  
Nouns and verbs hold great meaning in a sentence. A noun and verb is identified as the 2 keywords and if a noun or verb is not present, an adjective is chosen as a keyword.  
  
## In this repo  

* [Word2Vec](https://github.com/dhanyagowrish/Winograd-Schema-Challenge/tree/master/Word2Vec)  
Pre-trained Word2Vec word vectors were used for the keywords and antecedents.  
Two models, one trained on WSC-285 and the other on WinoGender  
  
* [GloVe](https://github.com/dhanyagowrish/Winograd-Schema-Challenge/tree/master/GloVe)  
GloVe word vectors were used for the keywords and antecedents.  
Two models, one trained on WSC-285 and the other on WinoGender  

* [ConceptNet](https://github.com/dhanyagowrish/Winograd-Schema-Challenge/tree/master/ConceptNet)  
ConceptNet relatedness value was used to find the similarity between keyword-antecedent pairs  
Two models, both trained on **WinoGender** dataset :  
**1.** Keywords identified using gensim keywords package [Method-1](https://github.com/dhanyagowrish/Winograd-Schema-Challenge/blob/master/ConceptNet/WinoGender-gensim-keywords.ipynb)  
  
    **2.** Keywords identified using [method previously explained](###keyword-identification) ie [Method 2](https://github.com/dhanyagowrish/Winograd-Schema-Challenge/blob/master/ConceptNet/WinoGender-hierarchy-method.ipynb)  
  
## Results  
**ConceptNet models**  
Method 1: 54.16 %  
Method 2: 65.21 %  
  
**Word2Vec Models**  
WSC-285: 48.0%  
WinoGender: 60.85%  
  
**GloVe Models**  
WSC-285: 56.86 %  
WinoGender: 54.16 %


