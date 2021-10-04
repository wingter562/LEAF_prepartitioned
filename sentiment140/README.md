## Pre-partitioned sentiment140 dataset

**Source data:** Sentiment140 Twitter (see http://help.sentiment140.com/for-students/ for details).

**Task**: sentiment analysis (binary classfication, NLP).

**Sampling and partitioning script**: ./preprocess.sh -s niid --sf 1.0 -k 30 -t sample (see [LEAF's repo](https://github.com/TalwalkarLab/leaf/tree/master/data/sent140) for details).

**Meta data**: 
- Sampling source: full data (--sf 1.0)
- User filter: number of samples >= 30 (-k 30)
- Statistically distribution: non-IID as each user is a unique domain (-s niid)
- Sampling results: number of users = 2875, number of samples = 146768
- Train/test split: 0.9/0.1

**Data format**: three key-value pairs at the top hierarchy, tweets data in the 3rd key-value pair as a dictionary.
- "users": the list of users
- "num_samples": the list of number of samples for each user
- "user_data": the corresponding value is a dictionary where keys correspond to usernames (listed in "users") and values correspond to a inner dict that contains two key-values:
  - "x": the tweets of the user as a nested list where the length of the outer list = the number of tweets by the user; the inner list records the metadata and data of each tweet:
    - treet id, e.g., "1932561653"
    - date and timestamp, e.g., "Tue May 26 21:43:20 PDT 2009"
    - query tag, e.g., "NO_QUERY"
    - username (same as the key in the "user_data" dict), e.g., "sunshine_diva"
    - tweet text, e.g., "@faithgoddess7 I love the outdoors...but mostly in the Spring and Fall. Not too cold or too hot... "
    - train/test tag, e.g., "training"
  - "y": the labels of the user's tweets as a list of binary values, e.g., \[1 1 1 1 1 1 1 1 1 1\].
