This section describes the end-to-end modelling steps performed for the Sequence to Sequence translation


DSDM_SEQ_TO_SEQ_Assignment_2.ipynb - is a basic seq to seq model built using the Spyder dataset.The model is trained and validated on the first 2000 records from training file of Spyder dataset. Some translation examples have been added at the end of the code explaining the effectiveness of the model



Pre-processing steps performed:

Data cleaning : converting to lowercase,removing punctuations,adding <sos><eos> tags in the sentences,Tokenization using Keras,Padding 
  
Pre-trained Glove embeddings used to convert the features to vectors.
  
Model - Seq to seq model built using LSTM (Both encoder and decoders have been LSTM based)

Encoder-Decoder models have been created to encapsulate the whole model for the translation purpose
  

translate_sentence,Custom function created to translated natural language to SQL
  

Please run each cell in order to execute the code

