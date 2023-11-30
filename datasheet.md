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

The model accepts three features.

### Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)?

_If so, please provide a link or other access point to the “raw” data._

### Is the software used to preprocess/clean/label the instances available?

_If so, please provide a link or other access point._

### Any other comments?

## Uses

_These questions are intended to encourage dataset creators to reflect on the tasks
for which the dataset should and should not be used. By explicitly highlighting these tasks,
dataset creators can help dataset consumers to make informed decisions, thereby avoiding
potential risks or harms._

### Has the dataset been used for any tasks already?

_If so, please provide a description._

### Is there a repository that links to any or all papers or systems that use the dataset?

_If so, please provide a link or other access point._

### What (other) tasks could the dataset be used for?

### Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses?

_For example, is there anything that a future user might need to know to avoid uses that
could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of
service issues) or other undesirable harms (e.g., financial harms, legal risks) If so, please
provide a description. Is there anything a future user could do to mitigate these undesirable
harms?_

### Are there tasks for which the dataset should not be used?

_If so, please provide a description._

### Any other comments?

## Distribution

### Will the dataset be distributed to third parties outside of the entity (e.g., company, institution, organization) on behalf of which the dataset was created? 

_If so, please provide a description._

### How will the dataset will be distributed (e.g., tarball on website, API, GitHub)?

_Does the dataset have a digital object identifier (DOI)?_

### When will the dataset be distributed?

### Will the dataset be distributed under a copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?

_If so, please describe this license and/or ToU, and provide a link or other access point to,
or otherwise reproduce, any relevant licensing terms or ToU, as well as any fees associated
with these restrictions._

### Have any third parties imposed IP-based or other restrictions on the data associated with the instances?

_If so, please describe these restrictions, and provide a link or other access point to, or
otherwise reproduce, any relevant licensing terms, as well as any fees associated with these
restrictions._

### Do any export controls or other regulatory restrictions apply to the dataset or to individual instances?

_If so, please describe these restrictions, and provide a link or other access point to, or otherwise
reproduce, any supporting documentation._

### Any other comments?

## Maintenance

_These questions are intended to encourage dataset creators to plan for dataset maintenance
and communicate this plan with dataset consumers._

### Who is supporting/hosting/maintaining the dataset?

### How can the owner/curator/manager of the dataset be contacted (e.g., email address)?

### Is there an erratum?

_If so, please provide a link or other access point._

### Will the dataset be updated (e.g., to correct labeling errors, add new instances, delete instances)?

_If so, please describe how often, by whom, and how updates will be communicated to users (e.g., mailing list, GitHub)?_

### If the dataset relates to people, are there applicable limits on the retention of the data associated with the instances (e.g., were individuals in question told that their data would be retained for a fixed period of time and then deleted)?

_If so, please describe these limits and explain how they will be enforced._

### Will older versions of the dataset continue to be supported/hosted/maintained?

_If so, please describe how. If not, please describe how its obsolescence will be communicated to users._

### If others want to extend/augment/build on/contribute to the dataset, is there a mechanism for them to do so?

_If so, please provide a description. Will these contributions be validated/verified? If so,
please describe how. If not, why not? Is there a process for communicating/distributing these
contributions to other users? If so, please provide a description._

### Any other comments?
