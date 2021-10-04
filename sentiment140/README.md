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
