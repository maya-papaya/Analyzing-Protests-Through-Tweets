# Analyzing Protests Through Tweets

In our modern society, protests are a way to collectively unite our voices to create change. However, some protests can negatively impact communities (looting, riots) or just be a nuisance (blocking traffic). Other times, people focus on the protesters' actions, rather than the message they're trying to spread (for example, the climate activists who threw soup at a famous painting). I wanted to find out how we can effectively share our voices through protests and gain support.

This project is meant to explore public sentiment toward protests by analyzing tweets.

I looked at two protests: the farmers' protest in India and the Women's March movement. Here's a little background on each:

### The Indian Farmers' Protest
The Indian farmers' protest lasted between 2020 and 2021. It was in response to laws passed by Prime Minister Narendra Modi which would minimize government involvement and instead encourage private investors. "More than 60 percent of India’s 1.3 billion people still depend primarily on agriculture for their livelihood, though the sector accounts for only about 15 percent of the country’s economic output," writes the New York Times, "For years, debts and bankruptcies have been driving farmers to high rates of suicide." Finally, the laws were repealed.

### Women's March
The Women's March movement began in 2017, the day after the inauguration of former President Donald Trump, due to his misogynistic rhetoric. It was recorded as the largest protest in U.S. history. Eventually, their mission adapted to include many issues - as the organization once said, "women's rights are human rights." Now, they have advocated on topics including "women's rights, immigration reform, healthcare reform, disability justice, reproductive rights, the environment, LGBTQ rights, racial equality, freedom of religion, workers' rights and tolerance" according to Wikipedia. To this day, they still arrange annual protests.

---

I divided my process into three parts: finding datasets, fine-tuning models, and finally conducting my analysis.

## Finding Datasets
I used a [HuggingFace dataset](https://huggingface.co/datasets/tweet_eval/viewer/sentiment/train) to train my model in sentiment analysis.

For the analysis, I chose two datasets from Kaggle ([Indian farmers' protest](https://www.kaggle.com/datasets/prathamsharma123/farmers-protest-tweets-dataset-csv) & [#WomensMarch movement](https://www.kaggle.com/datasets/adhok93/inauguration-and-womensmarch-tweets)).

## Fine-tuning the Models
I used two models: one as a [sentiment analyzer](https://huggingface.co/mayapapaya/Sentiment-Analyzer) and the other as a [keyword extractor](https://huggingface.co/mayapapaya/Keyword-Extractor).

## Conducting My Analysis
I had three functions:

* **Public Sentiment:** determines the majority sentiment towards the movement)

* **Public Sentiment within a certain time period (parameters: start_date, end_date):** determines whether a certain protest (for example, a riot) affects how the movement is viewed)

* **Keyword Extractor (parameters: keywords):** determines whether the issue itself is being spread, or whether the protester’s actions distract from that)
I had a list, keywords, that held all the keyword variations that are considered central to the movement (e.g., abortion keywords might include [“abortion”, “reproductive rights”, “pro-life”, “pro-choice”, etc.])

## Results

### The Indian Farmers' Protest

### Women's March

For the first function, I found the following:
```
Positive Tweets: 37.00666666666667 %
Negative Tweets: 44.4 %
Neutral Tweets: 18.593333333333334 %

Total Tweets: 15000
```
The slight majority is either unconcerned or supportive of the Women's March movement. About 44.4% are negatively geared toward it.

<img width="467" alt="Chart 1" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/b8aaa6e4-d691-473e-ad2c-1e7a1cc4e975">

For the second function, I decided to determine whether how the Women's March leader's actions ([see more in this article](https://time.com/5505787/womens-march-washington-controversy/) affected how the movement as a whole was viewed.
Here are my results:
```

```

For the last function, I found the following:
```

```


## Conclusion



