### Model Stealing Attack

#### Executive summary
This is a demonstration of a [model stealing](https://www.mlsecurity.ai/post/what-is-model-stealing-and-why-it-matters) (also known as model extraction) attack. This attack allows an adversary to create a copy a model without any access to the model's source code or training data. This is often a first step for an attacker who desires to perform more aggressive attacks such as evasion, inversion, or inference.

#### Rationale
Models often work with an organization's most sensitive data. Because the sensitive data and the model's source code are often kept private, organizations can erroneously assume that they are protected from cybersecurity threats. This project is a demonstration of the feasibility of stealing a machine learning model. 

#### Research Question
How feasible is a model stealing (model extraction) attack? What is the level of effort required?

#### Data Sources
To ensure this project's legality, I targeted a model whose author granted the public permission to steal it. [HackThisAI](https://github.com/JosephTLucas/HackThisAI/) contains a number of AI hacking challenges, many of them preserved from the infamous annual [Defcon](https://defcon.org) hacker conference. I have selected the ["Stonks"](https://github.com/JosephTLucas/HackThisAI/tree/main/challenge/medium_stonks) challenge, rated medium difficulty. My objective was to create a perfect copy of a black-box classification model, where I had no access to the model's code or data. This black-box model was simulated by a Docker image (available in the HackThisAI challenge) that I interacted with via a REST API.

The black-box model provides buy/sell recommendations based on stock market data, specifically a stock's daily open, close, high, low, and volume. This particular model is a classification model, not a time series.

#### Methodology
I created a dataset from public stock price data, and submitted it to the black-box model, and recorded its recommendations as the classification (my "y" values) I want my model to duplicate.

I tried four classification model types to create the stolen model: K-nearest neighbors, logistic regression, decision trees, and support vector machines.

#### Results
I demonstrated that I was able to create a 100% accurate copy of the target model without any access to its source code or training data. 

#### Next steps
In the future, I would like to target more sophisticated models. In particular, I would like to try to steal an image classification model, and then perform an evasion (misclassification) attack against my stolen copy of the model.

#### Outline of project

[Jupyter Notebook](https://github.com/hotpacket/modelstealing/blob/main/steal-stonks.ipynb)

