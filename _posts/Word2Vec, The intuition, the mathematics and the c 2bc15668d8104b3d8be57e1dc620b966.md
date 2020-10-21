# Word2Vec, The intuition, the mathematics and the code

Created: Oct 6, 2020 9:09 PM

Word Embeddings have been around for about 6 years now, so blog posts like this have also been around for the same time. And yet I think its a great idea to right another one because I am a moron. Lets get started. 

I am going to talk about the famous Word2Vec algorithm proposed by Mikolov et al. in their paper titled ***Distributed Representations of Words and Phrases and their Compositionality.*** The paper showed a great example displaying how the representations learned by their model is able to capture the salient features of the english language and semantic understanding using analogies as evidence. The famous example of "King" - "Man" + "Woman" = "Queen" is something that even the people living in the amazon forests have now probably heard. But to tell you the truth, before starting to write this blog post I had not the foggiest of ideas about the mathematical and practical details of this model. But I did promise that I will give you an intuition of what it is so lets start with that

### The Skip-Gram Model

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/skip-gram-data-image.png](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/skip-gram-data-image.png)

I would like to bring your attention to this shamelessly stolen image from Chris McCormick's [blog](https://mccormickml.com/2016/04/19/word2vec-tutorial-the-skip-gram-model/), which contains an obviously better written article. The text which brings back terrible memories from primary school english classes is our source text. We are interested in looking at a word and then trying to find out the words that are in its proximity. This is because a linguist named John Rupert Firth decided to be snarky and quote ***You shall know a word by the company it keeps.*** Consider the instance where the window cover "quick brown fox jumps over", here the blue marker lies on "fox" which is the target word, while the words "quick", "brown", "jumps" and "over" are known as the context words. Extracting this data is a secret tool that is going to help us later. 

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/secret-tool-help-us-later.jpg](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/secret-tool-help-us-later.jpg)

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/skip-gram-image.png](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/skip-gram-image.png)

---

We are going to talk about Word Embedding using Word2Vec. Developed by Google in 2013-14. Use Neural Networks. (Latent semantic analysis relevant here). (Word Embeddings + Context Embeddings)  

- Word2Vec
- CBOW
- Skip Gram
- One-Word Learning
- Input Layer
- Hidden Layer
- Output Layer
- Update
- CBOW - multiple Words
- Loss Function
- What does it learn?
- Skip-Gram Model
- Sub-Sampling
- Negative Sampling
- Softmax
- Hierarchical Softmax
- Limitations

### Goal

- Process each word in vocabulary to obtain a respective numeric representation of each word in the vocab
- Reflect semantic and syntactic similarities
- Map each of the plurality of words to a respective vector and output a single merged vector that is a combination of the respective vectors.

### Context Words and Central Word

CBOW: A central word is surrounded by context words. Given the context words, identify the central word 

Skip Gram Model- Given the central word, identify the surrounding words

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.04.37_PM.png](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.04.37_PM.png)

CBOW Architecture

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.06.40_PM.png](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.06.40_PM.png)

Skip-Gram Architecture

### One Word Learning

Add the window animation here

### Bowtie Models

![Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.11.54_PM.png](Word2Vec,%20The%20intuition,%20the%20mathematics%20and%20the%20c%202bc15668d8104b3d8be57e1dc620b966/Screenshot_2020-10-20_at_12.11.54_PM.png)

A CBOW model with only one word as input. The layers are fully connected. Here *W* and *W'* are learned

Mention One Hot Encoding 

### Forward Pass

**Hidden Layer**

$$h = W^TX $$

$$u_j = v_{w_{j}}^{'T}v_{w_{I}}$$

**Output Layer**

$$p(w_j|w_I) = y_j$$

where $y_j$ is the output of the $j^{th}$ unit in output layer

$$y_j = \frac{e^{u_j}}{\sum_{i'=1}^{V}e^{u_{j'}}}$$