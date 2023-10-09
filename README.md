# Sentiment-Analysis
Sentiment Analysis on IMDB Movie Review Dataset


IMDB Movie review, a dataset for binary sentiment classification has been downloaded and copied in a folder 
“aclImdb” present in the data directory. 
The aclImdb consists of 2 sub-folders: Train & Test.
The main aim of the report is to represent the data preprocessing steps, design choice for the network used to 
classify the review as negative or positive and the respective training & testing accuracies.

# Dataset:
The Imdb dataset contains 50,000 reviews split evenly into 25k train and 25k test sets. The overall distribution 
of labels is balanced with 25000 positive and negative labels respectively. In the labeled train/test sets, a 
negative review has a score <= 4 out of 10, and a positive review has a score >= 7 out of 10.

# Data Preprocessing:
1. The data was uploaded from the local directory by giving path of our directory and reading the text files 
along with their polarity (‘neg’ & ‘pos’) into train and test respectively.
2. Once the data was loaded the first step was to remove the special characters and any unwanted blank spaces 
from the reviews using regex.
3. Next, stopwords were removed from the reviews using the list of stopwords present in the nltk.corpus
module.
4. The reviews were then vectorized into a list of integers for feature extraction. The training data was then 
fitted on the Vectorizer () to create a dictionary of integer values with indexes of words present in the 
reviews.
5. The data was then converted into a list of sequences using the texts_to_sequence method of the Tokenizer 
().
6. Padding was done on the sequences generated to convert the input of varying length into sentences with 
same number of words. The sentences that had the words less than the max_length specified were appended 
with 0’s at the end and the sentences with extra words were cut.


# Sentiment Analysis Model:
1. Architecture/Design Choices:
 The model created for the Imdb dataset given is a CNN model with 5 layers:
- First layer is the embedding layer used to learn an embedding for all the words in the training dataset.
The layer has 2 input parameters:
• Vocab size – Length of the word index generated from the tokenizer
• Embedding Dimension – 16
- Second, we have Conv1D layer to perform the first convolution operation to filter the information and 
generate a feature map for feature extraction in the subsequent layers.
The parameters for this layer are:
• Filters – 64
• Kernel Size – 3
• Padding – Same
• Activation Function - Relu
- Next, we have the global average pooling layer(1D) to reduce the size of the input image so that less 
computations need to be performed on the input data.
The fourth layer is a Dense layer with 256 nodes and Relu activation function to convert the input from 
the convolution layer and give the output as required.
- The fifth layer is the output Dense layer with Sigmoid activation function to predict the sentiments for 
the input sentence provided.

# Accuracy Analysis:
- CNN model (Chosen Model)
Training Accuracy – 98.01%
Validation Accuracy - 89.45%
Testing Accuracy – 87.34%

# Bi-Directional LSTM
Training Accuracy – 92.4%
Validation Accuracy - 82.3%
Testing Accuracy – 83.7%
![image](https://github.com/jahnvidave04/Sentiment-Analysis/assets/126203211/3d433df0-a4ae-4453-b664-3641303be7cd)


![image](https://github.com/jahnvidave04/Sentiment-Analysis/assets/126203211/3617a739-484a-4f84-a26d-81bd6c30aca9)

From the results above, the training loss value for the CNN model was found out to be 0.0641 with an accuracy 
of 98.01. The accuracy for this model as available in the papers is 87-89%. For the model we created the testing 
accuracy was found out to be 87.34 that is very close to the range specified



