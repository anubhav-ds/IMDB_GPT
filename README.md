# IMDB GPT

This project features a local Causal llm trained on pytorch using imdb review dataset. We used Hugging Face for data preparation and Pytorch/Lightening for model training and evaluation. We performed extensive hyperparameter tuning and reduced the perplexity by ~22% after initial training. 

Model itself is limited to the dataset which inturn was limited to the local hardware. Nevertheless, with 50 million parameters only we were able to create a decent movie review generator natively.

After that, we finetuned TinyLlama 1.1B Chat model from Huging Face by using the QLoRA technique, training only 0.57% of the total paramters but with good results as even with prompt like "A " model was able to generate IMDB movie review. And while model loss and perplexity are not comparable because of different tokenizer methods we were able to obtain test perplexity of 15.35 in QLoRA optimized model, and in custom Causal LM we obtained perplexity of 97.27, while these metrics may not be comparable a visual test is indeed definitive evaluation metric on which finetuned model was much better than our local LLM, but considering that our custom LLM had only 50 million parameters its a good result from it considering limiteed 8GB local VRAM we had.

## Test Generation

**Prompt: Movie was Awesome! (max length = 100)**

Custom Causal LM: Movie was Awesome! I can't wait for something for it. I've just been the most talented director of his other films. And while I watch this one, I think you're a fan of the first movie. I was not expecting much, because I haven't seen it. It's a very very well made movie, and I don't think that you can't really care if it's going to be a good film, but I'll give it a try.<br /><br />The acting is also

QLoRA FineTuned TinyLlama: Movie was Awesome! In my opinion, this is one of the funniest movies ever made. The cast is exceptional, the story is very believable, and the acting is superb. As a movie, it is very well acted, written, and directed. One of the many reasons I rated this movie "10" is because it is very well acted, with a great cast. <br /><br />The story is about a very unstable woman who is in a coma (the movie was made in 1971) and when she wakes up

**Prompt: This movie was (max length = 300)**

Custom Causal LM: This movie was oot. I can't believe that the director had the opportunity to tell you why the film is all about. I mean, I would have liked to see the first two seasons before the first one, and they made it a long way into the series. But the writing was good, the ending was stupid and stupid, the acting was terrible. The problem was because it started with a good story and i couldn't. I still think this movie was directed by someone with a few good actors, but the way they turned it off was because of the real life in the movie was in it. The main character's character is so weird and the character is just totally different. The character really was terrible and the girl is cute. I think this movie isn't bad either, but not one of the worst movies ever made.<br /><br />If you're looking for a remake of the Dead in the Crypt, this movie's been made in a very early 90's movie. It's not a good movie because it's not an a movie. The plot is very good too, but sadly a mess of the first two movies are very touching. All the actors are very good. I saw this movie a lot better than that, but it was fun to watch. The plot is very good, but the actors are some of the dialogs are excellent, the acting, and the acting are great. There are so much better than the main characters who have the plot. The original plot is

QLoRA FineTuned TinyLlama: This movie was 100% great! <br /><br />It was the first movie I ever saw that had an American accent. I loved the accent, and even though I didn\'t know what was going to happen, I was still able to follow the story. I was really surprised when I watched the end. I thought it would be a typical movie ending like I\'ve seen in many other movies. But the ending was different. I was really surprised by it. There are many good things about this movie. Its beautiful color scheme. The cinematography is stunning. The music is beautiful. The photography is fantastic. It has a great story line. The movie itself is so beautiful and has so many great characters and scenes. The plot is very intriguing. I think that the movie is so great because the story is so captivating and the cinematography is so breathtaking. It is a great movie to watch in the evening. It is so beautiful that it is worth watching it more than once. I would definitely recommend this movie. It is a great movie that you should see and enjoy! I highly recommend this movie! It is a perfect film for people who love beautiful films with great acting and story lines. It is a very beautiful movie. I would give this movie a 10/10. This is not a typical "King of Kung Fu" film. The plot is not really

Prompt to test QLoRA training:

**Prompt: A (max length = 100)**

QLoRA FineTuned TinyLlama: A 3 out of 10 for this one.<br /><br />2. 'Mindhunter' A 3 out of 10 for this one.<br /><br />I was really looking forward to this movie. I had heard about the cast and crew and was looking forward to the story. The movie started promisingly but the end was predictable.<br /><br />If you love horror movies of the 1970's you'll love this one, but if you don't like the '70's then you

While both models are prone to rambling, there performance is acceptable considering the limited dataset and local hardware we used to make the models.
