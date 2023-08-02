# Analyzing Protests Through Tweets

In our modern society, protests are a way to collectively unite our voices to create change. However, some protests can negatively impact communities (looting, riots) or just be a nuisance (blocking traffic). Other times, people focus on the protesters' actions, rather than the message they're trying to spread (for example, the climate activists who threw soup at a famous painting). I wanted to find out how we can effectively share our voices through protests and gain support without disrupting the cause.

This project is meant to explore public sentiment toward protests by analyzing tweets.

I looked at two protests: the farmers' protest in India and the Women's March movement. Here's a little background on each:

### The Indian Farmers' Protest
The Indian farmers' protest lasted between 2020 and 2021. It was in response to laws passed by Prime Minister Narendra Modi which would minimize government involvement and instead encourage private investors. "More than 60 percent of India’s 1.3 billion people still depend primarily on agriculture for their livelihood, though the sector accounts for only about 15 percent of the country’s economic output," writes the New York Times, "For years, debts and bankruptcies have been driving farmers to high rates of suicide." Finally, the laws were repealed.

### Women's March
The Women's March movement began in 2017, the day after the inauguration of former President Donald Trump, due to his misogynistic rhetoric. It was recorded as the largest protest in U.S. history. Eventually, their mission adapted to include many issues - as the organization once said, "women's rights are human rights." Now, they have advocated on topics including "women's rights, immigration reform, healthcare reform, disability justice, reproductive rights, the environment, LGBTQ rights, racial equality, freedom of religion, workers' rights and tolerance" according to Wikipedia. To this day, they still arrange annual protests.

---

I divided my process into three parts: finding datasets, fine-tuning my model, and finally conducting my analysis.

## Finding Datasets
I used a [HuggingFace dataset](https://huggingface.co/datasets/tweet_eval/viewer/sentiment/train) to train my model in sentiment analysis.

For the analysis, I chose two datasets from Kaggle ([Indian farmers' protest](https://www.kaggle.com/datasets/prathamsharma123/farmers-protest-tweets-dataset-csv) & [#WomensMarch movement](https://www.kaggle.com/datasets/adhok93/inauguration-and-womensmarch-tweets)).

## Fine-tuning the Model
I used finetuned my model to be a [sentiment analyzer](https://huggingface.co/mayapapaya/Sentiment-Analyzer).

## Conducting My Analysis
I had three functions:

* **Public Sentiment:** determines the majority sentiment towards the movement)

* **Public Sentiment within a certain time period (parameters: start_date, end_date):** determines whether a certain protest (for example, a riot) affects how the movement is viewed)

* **Keyword Extractor (parameters: keywords):** determines whether the issue itself is being spread, or whether the protester’s actions distract from that)
I had a list, *keywords*, that held all the keyword variations that are related to a protest rather than the movement itself (e.g., keywords like "protest", "riot", "nuisance", "traffic", "problem", etc.). For this function, I used a KeyBERT model ([learn more here](https://sparkbyexamples.com/python/sort-using-lambda-in-python/)) to extract keywords.

---
Here were the results and conclusions I drew from my analysis:

## Results

### The Indian Farmers' Protest

The overall sentiment on Twitter towards the Indian farmers' protest is as shown:
```
Positive Tweets: 24.312463806604626 %
Negative Tweets: 34.93026892845419 %
Neutral Tweets: 40.75726726494119 %

Total Tweets: 1,084,452
```
<img width="488" alt="Indian Farmers' Protest Chart 1" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/4f911e58-53b4-4374-94f2-9a831024186d">

The majority (about 65%) is either unconcerned or supportive of the Indian farmers' protest. About 34.9% are negatively geared toward it.

For the second function, I decided to look at a specific instance where, "[on 29 November, the protesters announced that they would block five further points of entry into Delhi,](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" according to Wikipedia. Despite [overwhelming support for India's farmers](https://foreignpolicy.com/2021/11/28/farmers-protests-india-martyrs/), I was curious to see whether people would view this as a nuisance or support it.
```
Positive Tweets: 23.153694019608533 %
Negative Tweets: 41.60725220120917 %
Neutral Tweets: 35.2390537791823 %

Total Tweets: 426,243
```
<img width="468" alt="Indian Farmers' Protest Chart 2" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/72ea8930-dbe2-48ae-99b2-898905294d68">

The percentage of negative tweets increases by almost 7%. Perhaps there was a slightly more negative reaction.

I also thought that a certain instance where "a farmer's protest on 5 November turned violent and a MP's car window was smashed," according to Wikipedia, would be interesting to investigate.
```
Positive Tweets: 20.450916059347872 %
Negative Tweets: 38.10864957463488 %
Neutral Tweets: 41.44043436601725 %

Total Tweets: 68,882
```
<img width="474" alt="Indian Farmers' Protest Chart 3" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/f2d3732d-0ae4-4bdd-be56-e85e760d60e7">

This time, the percentage of negative tweets only increases by less than 4%. Since one smashed car window is more irrelevant to most people's lives and it's easier to distance one's self from that circumstance, it's possible that there was a less negative reception.

During the Republic Day protest, "[the violence and hoisting of a religious flag on the ramparts of the Red Fort made the Bharatiya Kisan Union (Bhanu) and All India Kisan Sangharsh Co-ordination Committee decide to quit the farmers' protest.](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" I wondered if that specific protest (combined with how "several metro stations were closed and mobile internet was suspended by police") affected the sentiment towards the protest.
```

```

For the last function, I found the following:
```

```


### Women's March

For the first function, I found the following:
```
Positive Tweets: 37.00666666666667 %
Negative Tweets: 18.593333333333334 %
Neutral Tweets: 44.4 %

Total Tweets: 15,000
```
<img width="482" alt="Women's March Protest Chart 1" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/35b97e1e-67c3-4862-a3db-7452a4fbccd1">

The overwhelming majority (about 81.4%) is either unconcerned or supportive of the Women's March movement. About 18.6% are negatively geared toward it. This result is unsurprising considering that this dataset only covers tweets from the first Women's March. However, since the movement's leaders became wrapped up in [several controversies](https://time.com/5505787/womens-march-washington-controversy/), I wonder how that number would change now.

For the last function, I found the following:
```
Keywords: "riot", "nuisance", "traffic", "problem"
Percentage: 0.0 %
```
This result makes sense considering both the dataset's limits and how the overwhelming majority was positively inclined toward the movement. The dataset only included tweets with the tag, #FarmersProtest, so it's likely that not many tweets within the dataset obviously criticized the movement.

## Conclusion

### The Indian Farmers' Protest

Twitter notably had to jump hurdles with [the Indian government](https://www.npr.org/2021/02/17/968641246/twitter-in-standoff-with-indias-government-over-free-speech-and-local-law) about suppressing the backlash against the farm laws. Accounts were suspended at first and hashtags were reduced. As Twitter struggled between free speech and the government's orders, I wonder if this affected the results somehow.

<img width="30%" alt="Indian Farmers' Protest Chart 1" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/4f911e58-53b4-4374-94f2-9a831024186d">
<img width="30%" alt="Indian Farmers' Protest Chart 2" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/72ea8930-dbe2-48ae-99b2-898905294d68">
<img width="30%" alt="Indian Farmers' Protest Chart 3" src="https://github.com/maya-papaya/Analyzing-Protests-Through-Tweets/assets/116525763/f2d3732d-0ae4-4bdd-be56-e85e760d60e7">

However, the majority seems to be in support of the Indian farmers who are protesting. The only time that the percentage of negative tweets changed was when [some of the entrances to Delhi were blocked](https://indianexpress.com/article/cities/chandigarh/farmers-protest-msp-block-delhi-chandigarh-highway-8660023/). This may indicate that people prefer to support protests that don't interfere with their mobility. In fact, violence against one politician caused less of a change than the traffic and rerouting caused by the protest.

### Women's March

The Women's March (at least at its first protest) seems to be greatly supported. However, I think it would be an interesting project in the future to research how they are viewed today.

### As a whole...

Protests seem to be most effective when they don't hinder daily activities (causing traffic, blocking entrances, etc.). Violence or unnecessarily brutal actions can also negatively impact a movement, even if that violence was only caused by one person.


***Notes:***
*This project is not verified or error-free. Please use results with caution. The Google Colab notebooks and HuggingFace/KeyBERT models used to create this research project are available for further analysis.*



