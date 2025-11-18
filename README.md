# IMDB GPT

This project features a local Causal llm trained on pytorch using imdb review dataset. We used Hugging Face for data preparation and Pytorch/Lightening for model training and evaluation. We performed extensive hyperparameter tuning and reduced the perplexity by ~22% after initial training. 

Model itself is limited to the dataset which inturn was limited to the local hardware. Nevertheless, with 50 million parameters only we were able to create a decent movie review generator natively.
