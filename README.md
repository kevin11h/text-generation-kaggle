> It's been awhile so I don't remember the specifics, but I may have used conda forge and conda environments to install tensorflow then keras. I apologize if that's not super helpful

https://gist.github.com/rexlow/93123f8003e3085d51316ede73c23d6d

bash Miniconda3-latest-MacOSX-x86_64.sh

// append env path

conda install jupyter matplotlib pandas scipy Pillow scikit-learn

conda install -c conda-forge keras tensorflow

// for some reasons tensorflow installed = 1.0.0, update here

conda update -f -c conda-forge tensorflow

conda install -c conda-forge opencv

# https://towardsdatascience.com/simple-text-generation-d1c93f43f340
# https://towardsdatascience.com/text-classification-in-keras-part-1-a-simple-reuters-news-classifier-9558d34d01d3
# https://towardsdatascience.com/text-classification-in-keras-part-2-how-to-use-the-keras-tokenizer-word-representations-fd571674df23

# Text Generation: Stacked LSTM's to generate text in the style Edgar Allen Poe

**Jeremy Chow**

7/15/2019

Goal: Generate text in the style of Edgar Allen Poe, specifically emulating his writing style in the short story dataset from Kaggle "Spooky Author Identification" competition: https://www.kaggle.com/c/spooky-author-identification 

# Model Architecture:
1. Embedding layer
    - Helps model understand 'meaning' of words by mapping them to representative vector space instead of semantic integers
2. Stacked LSTM layers
    - Stacked LSTMs add more depth than additional cells in a single LSTM layer (see paper: https://arxiv.org/abs/1303.5778)
    - The first LSTM layer must have `return sequences` flag set to True in order to pass sequence information to the second LSTM layer instead of just its end states
3. Dense (regression) layer with ReLU activation
4. Dense layer with Softmax activation 
    - Outputs word probability across entire vocab

# Example Output:

**Input:** `First of all I dismembered the corpse`

**Model:**

"First of all i dismembered the corpse which is profound since in the first place he appeared at first so suddenly as any matter no answer was impossible to find my sake he now happened to be sure it was he suspected or caution or gods and some voice held forth upon"
