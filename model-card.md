# Model Stealing Model Card

Last updated: November 2023

Inspired by [Model Cards for Model Reporting (Mitchell et al.)](https://arxiv.org/abs/1810.03993).

## Model Details

This is a demonstration of a model stealing (also known as model extraction) attack. This attack allows an adversary to create a copy a model without any access to the model's source code or training data. This is often a first step for an attacker who desires to perform more aggressive attacks such as evasion, inversion, or inference.

There are two models to consider with this project, the original, "victim" model targeted for stealing, and the "stolen," or duplicated model.

The victim model provides buy/sell recommendations based on stock market data, specifically a stock's daily open, close, high, low, and volume. The author of this model has granted the public permission to steal it as a cybersecurity exercise. This victim model was available as a Docker image (downloaded [here](https://github.com/JosephTLucas/HackThisAI/tree/main/challenge/medium_stonks)) that I interacted with via a REST API.

### Model date

Stolen Model: November 2023<br> 
Victim Model: December 2021

### Model type

Binary classification model

## Model Use

The victim model is ostensibly used for buy/sell recommendations based on stock market information, though its true purpose is as a cybersecurity exercise to promote machine learning security awareness.

Models often work with an organization's most sensitive data. Because the sensitive data and the model's source code are often kept private, organizations can erroneously assume that they are protected from cybersecurity threats. This project is a demonstration of the feasibility of stealing a machine learning model.

## Data, Performance, and Limitations

### Data 

I created datasets from public stock price data for the last 4 years (NVDA.csv and AAPL.csv), and submitted it to the black-box model, and recorded its recommendations as the classification (my "y" values) I wanted my model to duplicate.

### Performance 

The final version of the stolen model successfully duplicated the victim model on all of the test data (100% accuracy). 

## Limitations


