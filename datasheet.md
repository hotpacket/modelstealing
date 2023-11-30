# Datasheet for datasets "AAPL.csv" and "nvidia.csv"

Questions from the [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) paper, v7.

Jump to section:

- [Motivation](#motivation)
- [Composition](#composition)
- [Collection process](#collection-process)
- [Preprocessing/cleaning/labeling](#preprocessingcleaninglabeling)
- [Uses](#uses)
- [Distribution](#distribution)
- [Maintenance](#maintenance)

## Motivation

As a cybersecurity exercise, I attempted to "steal" a "victim" model. The victim model was a black-box Docker image that I interacted with via a REST API. I needed to feed appropriate data to the victim model so I could record its predictions.

### For what purpose was the dataset created? 

I created these datasets to analyze the behavior of HackThisAI's ["Stonks"](https://github.com/JosephTLucas/HackThisAI/tree/main/challenge/medium_stonks) model.

### Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)?

I created the datasets for my own use.

### Who funded the creation of the dataset? 

No funding was necessary.

## Composition

### What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?

The dataset consists of publicly-available trading data for the Nvidia and Apple stocks. 

### How many instances are there in total (of each type, if appropriate)?

There are 1007 rows per dataset.

### Does the dataset contain all possible instances or is it a sample (not necessarily random) of instances from a larger set?

The data covers every trading day between October 1, 2019 and September 30, 2023. 

### What data does each instance consist of? 

Date, daily open price, daily high price, daily low price, daily close price, daily volume.

### Is there a label or target associated with each instance?

The label is not included in the dataset, it must be obtained by querying the victim model. The victim model provides a label of 1 ("buy" recommendation) or -1 ("sell recommendation).

### Is any information missing from individual instances?

No.

### Are relationships between individual instances made explicit (e.g., users’ movie ratings, social network links)?

"AAPL.csv" contains the stock data for Apple and "nvidia.csv" contains the stock data for Nvidia.

### Are there recommended data splits (e.g., training, development/validation, testing)?

During testing, I found that the following split (test_size=0.3 and random_state=22) provided the best results:<br>
X_train, X_test, y_train, y_test = train_test_split(df[['oc','hl','vol']], df['y'], test_size=0.3, random_state=22)


### Are there any errors, sources of noise, or redundancies in the dataset?

No.

### Is the dataset self-contained, or does it link to or otherwise rely on external resources (e.g., websites, tweets, other datasets)?

Self-contained.

### Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by doctor-patient confidentiality, data that includes the content of individuals’ non-public communications)?

No.

### Does the dataset contain data that, if viewed directly, might be offensive, insulting, threatening, or might otherwise cause anxiety?

No.

### Does the dataset relate to people? 

No.

### Does the dataset identify any subpopulations (e.g., by age, gender)?

No.

### Is it possible to identify individuals (i.e., one or more natural persons), either directly or indirectly (i.e., in combination with other data) from the dataset?

No.

### Does the dataset contain data that might be considered sensitive in any way (e.g., data that reveals racial or ethnic origins, sexual orientations, religious beliefs, political opinions or union memberships, or locations; financial or health data; biometric or genetic data; forms of government identification, such as social security numbers; criminal history)?

No.

### Any other comments?

No.

## Collection process

### How was the data associated with each instance acquired?

I obtained the data from Yahoo Finance, using its "export to CSV" capability.

### What mechanisms or procedures were used to collect the data (e.g., hardware apparatus or sensor, manual human curation, software program, software API)?

Downloaded from Yahoo Finance website.

### If the dataset is a sample from a larger set, what was the sampling strategy (e.g., deterministic, probabilistic with specific sampling probabilities)?

I downloaded 4 years of trading data for Nvidia and Apple stocks.

### Who was involved in the data collection process (e.g., students, crowdworkers, contractors) and how were they compensated (e.g., how much were crowdworkers paid)?

I was the sole creator.

### Over what timeframe was the data collected?

I collected the data in October 2023.

### Were any ethical review processes conducted (e.g., by an institutional review board)?

No, the data is entirely public.

### Does the dataset relate to people?

No.

### Did you collect the data from the individuals in question directly, or obtain it via third parties or other sources (e.g., websites)?

### Were the individuals in question notified about the data collection?

N/A

### Did the individuals in question consent to the collection and use of their data?

N/A

### If consent was obtained, were the consenting individuals provided with a mechanism to revoke their consent in the future or for certain uses?

N/A

### Has an analysis of the potential impact of the dataset and its use on data subjects (e.g., a data protection impact analysis) been conducted?

N/A

### Any other comments?

No.

## Preprocessing/cleaning/labeling

_The questions in this section are intended to provide dataset consumers with the information
they need to determine whether the “raw” data has been processed in ways that are compatible
with their chosen tasks. For example, text that has been converted into a “bag-of-words” is
not suitable for tasks involving word order._

### Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)?

The model has three features:<br>

- OC - Open price minus close price (per day)
- HL - High price minus low price (per day)
- VOL - Daily volume

I computed OC and HL from the datasets before sending requests to the victim model.

### Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?

The nvidia.csv and AAPL.csv datasets are raw datasets.

### Is the software used to preprocess/clean/label the instances available?

Yes, the code is in the Jupyter notebook.

### Any other comments?

After preprocessing and adding the labels, the datasets were saved as "stonks-saved.csv" (Nvidia) and "stonks-saved2.csv" (Apple). I made these datasets are available for use in this repository, which makes interacting will the Docker image optional.

## Uses

### Has the dataset been used for any tasks already?

Yes, the datasets were used to completed the "model stealing" project in this repository.

### Is there a repository that links to any or all papers or systems that use the dataset?

Yes, [here](https://github.com/hotpacket/modelstealing/).

### What (other) tasks could the dataset be used for?

Other stock prediction models.

### Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses?

No.

### Are there tasks for which the dataset should not be used?

No.

### Any other comments?

No.

## Distribution

### Will the dataset be distributed to third parties outside of the entity (e.g., company, institution, organization) on behalf of which the dataset was created? 

The datasets consist of entirely public data. They will remain available in this repository.

### How will the dataset will be distributed (e.g., tarball on website, API, GitHub)?

[GitHub](https://github.com/hotpacket/modelstealing/).

### When will the dataset be distributed?

### Will the dataset be distributed under a copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?

No.

### Have any third parties imposed IP-based or other restrictions on the data associated with the instances?

No.

### Do any export controls or other regulatory restrictions apply to the dataset or to individual instances?

No.

### Any other comments?

## Maintenance

_These questions are intended to encourage dataset creators to plan for dataset maintenance
and communicate this plan with dataset consumers._

### Who is supporting/hosting/maintaining the dataset?

I am.

### Is there an erratum?

No.

### Will the dataset be updated (e.g., to correct labeling errors, add new instances, delete instances)?

No.

### If the dataset relates to people, are there applicable limits on the retention of the data associated with the instances (e.g., were individuals in question told that their data would be retained for a fixed period of time and then deleted)?

N/A

### Will older versions of the dataset continue to be supported/hosted/maintained?

No.

### If others want to extend/augment/build on/contribute to the dataset, is there a mechanism for them to do so?

GitHub fork.

### Any other comments?

No.
