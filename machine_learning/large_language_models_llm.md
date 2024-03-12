# The LLMs
- Large Language Models train on huge amounts of data with the aim to learn all the conditional conditions to allow them to generalize and generate meaning, without direct memorization of the training data. The LLM's knowledge is restricted to it's training set. 

- Thus if a model is trained up to 2023, like ChatGPT, then you ask something about 2023, this may generate a plausible but fabricated description. This is known as a "hallucination". So accuracy and reliability are paramount in things like chatbots, knowledge-based assistants, or AI tutorsz

- You invoke 










LLMs and NLP


Capabilites and Limitations of LLMs

Hallucinations and Bias in LLMs


Mitigating Risk of Hallucinations
- Improve data quality using various techniques to detect and correct inaccuracies, incorporate external knowledge bases for real-time updates, applying human-in-the-loop for oversight and corrections, and developing more sophisticated algorithms to better understand context and factual accuracy. 
- Use retrievers in tandem with LLMs. A retriever fetches relevant information from trusted sources, then the LLM is prompted to rearrange the information without inventing additional details, ensure to check your context window sizes to facilitate inclusion of multiple documents into a single prompt. GPT-4 and Claude can handle context windows of 32k and 100k tokens. (approx 20k words and 40 pages). Cost is a factor with the number of tokens, so using an efficient retriever to find the more relevant document is key. 

Concepts and Techniques:



Generating predictions:

Real world Application: