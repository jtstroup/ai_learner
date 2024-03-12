# General Principles of NLP
- Tokens
-- Where you break down language into components, attach numbers to them, so the machine can process the information. This is known as preprocessing or tokenization
- Token Approaches
-- Normalizing text
--- Removing punctuation, low value words like 'the'
-- Stemming
--- This is where we reduce words to the root form, so payment or repay to 'pay'
-- tagging parts of speech
--- Analyze words in their grammatical forms, words, noun, pronoun, verb
-- Entity recognition
--- About creating a taxonomy of location, persons, organizations
-- Topic modelling
--- This is creating structured data from a collection of unstructured data

- Recurrent Neural Networks (RNNs)
-- "I" "like" "pizza" 
-- RNN then turns a word like "I", into a numeric value
-- Then the output includes the next word "like" and includes the value "I" and placed in another RNN
-- This happens again to the next RNN with all the values "I", "like", "pizza"
-- We are finding the pattern to use all the words, not just one. 
-- Overtime we started refining with Long short-term memory (LSTM) models, these techniques still had issue with large amounts of information and  you could not use parallel processing, because it was processing one word at at time.
- Emergence of attention models
-- This is where a the model Analyzed the text and keys on the most relevant information and discards the rest
# Word2Vec Model (https://arxiv.org/pdf/1301.3781.pdf) (2013)
- Built word embeddings which is the encode words and numeric values for an AI system to work with. This provides better understand of the context of the words.  
- Each word is process with a Neural network to get context
- Works on windows!
- Processing works like
-- "The" --> "The dog jumps on my lap" 
-- "dog" --> "The dog jumps on my lap"
-- "jumps" --> "The dog jumps on my lap"

-- first pass will have the first two words "The" "dog", because it's first there is no prior two words
-- second pass will have the index move to dog and takes the next two words on the right "The dog jumps on" and the previous word "the"
-- third pass will have the index move to jumps and next two words are "on my" and the past two words are "the dog" 
-- This allows tagging with a number or weight to be added and increase large text. 
# Positional Encoding (multiheaded attnetion)
- "The" --> [0.11],[-13],[1.33] -- > 1 - "The" 
- "dog" --> [-0.15],[-1.22],[3.1] -- > 2 - "dog" 
- "jumps" -->[-0.18],[-1.19],[3.33] -- > 3 - "jumps"
- "!" --> [-0.23],[2.1],[2.13] -- > 4 - "!"

# Multi-headed attention
- The bank account earned interest
- J showed interested in book


# Emergence of Transformer model (https://arxiv.org/pdf/1706.03762.pdf) 
- transformer has an encoder and decoder, each is made up from multiple layers of self-attention and feedforward neural networks. 
- Self-attention: weigh the importance of words to different words in a sesntence based on affinity with each other. Thus having the AI focus on the most relevant parts of text rather then reading it linearly
- Positional bias - allows model to keep track of relative positions of words in a sentence. This is important because the order of words in a sentence can significantly impact meaning.
- Encoder-Decoder An input sentence goes through the encoder blocks, and produces a fixed-size vector representation of it, which is fed to the decoder to generate the output sentence. The decoder uses both self-attention and cross-attention, where the attention mechanism is applied to the output of the encoder and input of the decoder. 
-- One of the most popular is the T5 (Text-to-Text Transfer Transformer), introduced by Google in 2019 to find-tune for a wide range of NLP tasks, including language translation, question answering, summarlization, and more. 
-- Real world example of this architecture is Google Translate.
- One of the most popular transformer encoder models is BERT (Bidirectional Encoder Reprsentations from Transformers), which was introduced from Google in 2018. This transformer encoder is only concerned with the input sequence and does not generate any output sequence. It applies self-attention mechansism to the input tokens, allowing it to focus on the most relevant parts of the input for the given task. Real world is using this for sentiment analysis, where the model must classify given review as positive or negative, and email spam detection, where model must classify a given email as spam and not spam.
# GPT-3/4 
- one of the most popular transformer decodedr models. Generative Pre-trained Transfomer 3/4, introduced by OpenAI, a massive language model that can generate human-like text in a wide range of styles and genres. 
- Open AI used a technique called triangle masking for attention, whichi ensures the attention mechanism looks at tokens to the left of the current token being generated. this prevents the model from cheating by looking at tokens that it hasn't generated yet. the real-world of this included text generation, to generate a story or article based on a given prompt or topic, and chatbots, where the model must generate responses to user inputs in a natural and engaging way. 
# Drawbacks of Transformers
- High computation costs for the attention mechnasim based on sequence length
- Difficulty in interpretation and debugging because the attention model is locked over the entire input sequence
- Prone to overfitting when fine-tuned on small amounts of task-specific data

# A Transformer Process
- Input sequence - convert to embeddings (with positional encoding) and feed to next encoder
- A stack of encoders are created and process everything and produces an encoded represntaion of the input sequence
- The target sequence is prepended with a start-of-sentence token, converted into embeddings (with pos enc) and fed to the decoders
- Stack of decoders process this along with encoder stack representation to produce an encoded representation of target sequence
- The output layer converts it into word probabilities and the final output sequence
- Transformers Loss function compares this output sentence to target sequence from training data. This loss is used to generate gradiente to train the transformer during back-propagation

# Inference
- This is where we don' have the target sequence to pass as input to the decoder, so in a Seq2Seq model, we generate the output in a loop and feed the output sequence from previous timestep to decoder in next timestep until end-of-sentence token, the difference from Seq2Seq is at each timestep we re-feed the entire output sequence generated thus far, rather then just last word
- Input sequence - convert to embeddings (with positional encoding) and feed to next encoder
- A stack of encoders are created and process everything and produces an encoded represntaion of the input sequence
- ```instead of target sequence```, we use empty sequence with only start of sentence token, converted to emb
- Stack of decoders process this along with encoder stack representation to produce an encoded representation of target sequence
- The output layer converts it into word probabilities and the final output sequence
- Take last word out of output seence as predicted work, that word is filled into second postion 
- Transformers Loss function compares this output sentence to target sequence from training data. This loss is used to generate gradiente to train the transformer during back-propagation
