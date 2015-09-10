# python-topic-indexer
Python scripts to build a text topic classifier.

Current state: prototype
Categories are from (http://www.iab.net/QAGInitiative/overview/taxonomy)
Currently classification is based on *Tier 1* categories.

# Labeled data gathering
Since there is no labeled datasets for the categories I wanted, I've decided to start with quick solution:
**news_extractor.py** searches Google News for the *Tier 2* names, related articles (100 per Topic) are used in learner labeled with corresponding *Tier 1* category. 

Usage of *Tier 2* names dirrectly in search causes sometimes noisy results, for example search for **Collecting** ( "Hobbies & Interests" category) results in articles like:
 - Driver kills firefighter collecting for charity...
 - Man admits collecting $275K in dead mother's NYS benefits
 - Woman pleads guilty to trapping people in basement, collecting their disability checks
Too much for a hobby :)

Dataset quality hits dirrectly on the classifier performance. Further improvement will be either in search of better speudo-tagged source, or in the dirrection of heavier unsupervised algorythms.

# Algorythms
Text is cleaned up and stemmed by filters.
For performance I've used only  **scikitlearn** algorithm implementations.
Tested algorithms accuracy comparison, for ~7000 trained docs:
 - 0.850 Linear SVC
 - 0.760 Bernoulli Naive Bayes
 - 0.485 Multinominal Naive Bayes
