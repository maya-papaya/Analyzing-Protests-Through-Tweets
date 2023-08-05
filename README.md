# Analyzing Protests Through Tweets

In our modern society, protests are a way to collectively unite our voices to create change. However, some protests can negatively impact communities (looting, riots) or just be a nuisance (blocking traffic). Other times, people focus on the protesters' actions, rather than the message they're trying to spread (for example, the climate activists who threw soup at famous paintings). 

Still, experts say that [confrontational protests](https://grist.org/protest/confrontational-climate-protests-civil-disobedience-soup-van-gogh/) are an effective way to bring attention to a cause and portray less-bold protests in a better light. While this form of protest, called 'civil disobedience,' often is ineffective at garnering support for a movement, it has been a large part of effective social movements. Unfortunately for protestors, they have to choose between peaceful protests (usually ignored by the public) or civil disobedience (gaining the attention of the public and broadcasted by the media). The whole point of these confrontational protests *is* to make the public uncomfortable and force them into decisions. Social disruption has been a powerful tactic for very long: even suffragettes once slashed paintings and irreparably damaged them as a form of protest. Nowadays, civil disobedience is a tactic that has become increasingly popular among younger activists. A spokesperson from Just Stop Oil said, “We’re going to be noisy. We’re going to be disruptive. We’re going to be unignorable. We’re going to be a pain in the ass until you listen to us.”

However, the reality is that what constitutes an effective protest is a highly disputed topic. This is why I wanted to find out how we can effectively share our voices through protests and gain support without disrupting the cause.
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

* **Public Sentiment:** determines the majority sentiment towards the movement

* **Public Sentiment within a certain time period (parameters: start_date, end_date):** determines whether a certain protest (for example, a riot) affects how the movement is viewed

* **Keyword Extractor (parameters: keywords):** determines whether the issue itself is being spread, or whether the protester’s actions distract from that. I had a list, *keywords*, that held all the keyword variations that are related to a protest rather than the movement itself (e.g., keywords like "riot", "nuisance", "traffic", "problem", etc.). For this function, I used a KeyBERT model ([learn more here](https://sparkbyexamples.com/python/sort-using-lambda-in-python/)) to extract keywords.

Here were the results and conclusions I drew from my analysis:

## Results

### The Indian Farmers' Protest

The overall sentiment on Twitter towards the Indian farmers' protest is as shown:
```
Overall Sentiment:

Positive Tweets: 24.312463806604626 %
Negative Tweets: 34.93026892845419 %
Neutral Tweets: 40.75726726494119 %

Total Tweets: 1,084,452
```
<img width="600" alt="Indian Farmers' Protest Chart 1" src="Screenshot 2023-08-05 at 10.05.24 AM.png">


The majority (about 40.7%) is unconcerned or neutral towards the Indian farmers' protests. About 34.9% are negatively geared toward it. The minority of tweets are supportive towards the movement.

---

For the second function, I decided to look at a specific instance where on November 29th, "[the protesters announced that they would block five further points of entry into Delhi,](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" according to Wikipedia. Despite [overwhelming support for India's farmers](https://foreignpolicy.com/2021/11/28/farmers-protests-india-martyrs/), I was curious to see whether people would view this as a nuisance or support it.
```
Between 11-29-2020 and 03-22-2021:

Positive Tweets: 25.4336761614079 %
Negative Tweets: 34.31111038955768 %
Neutral Tweets: 40.25521344903443 %

Total Tweets: 615,955
```
<img width="600" alt="Indian Farmers' Protest Chart 2" src="Screenshot 2023-08-05 at 10.04.43 AM.png">

The percentage of negative tweets decreases by 0.6%, while the percentage of positive tweets increases by 1%. There is almost no change between the total public sentiment and this instance.

---

I also thought that a certain instance where "a farmer's protest on 5 November turned violent and a MP's car window was smashed," according to Wikipedia, would be interesting to investigate.
```
Between 11-05-2021 and 11-21-2021:

Positive Tweets: 27.842227378190255 %
Negative Tweets: 33.75259494443766 %
Neutral Tweets: 38.40517767737208 %

Total Tweets: 24,567
```
<img width="600" alt="Indian Farmers' Protest Chart 3" src="Screenshot 2023-08-05 at 10.03.37 AM.png">

This time, the percentage of negative tweets decreases by 1%, while the percentage of positive tweets increases by 3%. Since one smashed car window is more irrelevant to most people's lives and it's easier to distance one's self from that circumstance, it's possible that there was a less negative reception.

---

During the Republic Day protest, "[the violence and hoisting of a religious flag on the ramparts of the Red Fort made the Bharatiya Kisan Union (Bhanu) and All India Kisan Sangharsh Co-ordination Committee decide to quit the farmers' protest.](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" I wondered if that specific protest (combined with how "several metro stations were closed and mobile internet was suspended by police") affected the sentiment towards the protest.
```
Between 01-26-2021 and 02-01-2021:

Positive Tweets: 13.413878562577446 %
Negative Tweets: 48.213548120611314 %
Neutral Tweets: 38.372573316811234 %

Total Tweets: 38,736
```
<img width="600" alt = "Indian Farmers' Protest Chart 4" src="Screenshot 2023-08-05 at 10.02.30 AM.png">

For this instance, the percentage of positive tweets dramatically decreases to 13%, while the percentage of negative tweets increases to almost 50%. These prominent changes may be because of the violence that occurred. Two major groups decided to leave the farmers' protest because of the violence and religious flag. Likely, many people (including previous supporters of the movement) criticized the violence and the group of protesters who abandoned the original peaceful protest plan. Another factor contributing to the lack of positive support is the internet shutdown that caused farmers to lose contact with their supporters.

However, some of the negative tweets were likely also directed towards the government and their treatment of the farmers, as well as their crackdown on the internet/social media.

---

For the last function, I found the following:
```
Keywords: "riot", "nuisance", "traffic", "problem"
Percentage: 0.008667972395274295 %
Number of Tweets with Keywords: 94
```
So it turns out that people care more about the movement's causes rather than how it inconveniences them.

---

### Women's March

For the first function, I found the following:
```
Positive Tweets: 37.00666666666667 %
Negative Tweets: 18.593333333333334 %
Neutral Tweets: 44.4 %

Total Tweets: 15,000
```
<img width="600" alt="Women's March Protest Chart 1" src="Screenshot 2023-08-05 at 10.01.24 AM.png">


The overwhelming majority (about 81.4%) is either unconcerned or supportive of the Women's March movement. About 18.6% are negatively geared toward it. This result is unsurprising considering that this dataset only covers tweets from the first Women's March. However, since the movement's leaders became wrapped up in [several controversies](https://time.com/5505787/womens-march-washington-controversy/), I wonder how that number would change now.

---

For the last function, I found the following:
```
Keywords: "riot", "nuisance", "traffic", "problem"
Percentage: 0.0 %
```
This result makes sense considering both the dataset's limits and how the overwhelming majority was positively inclined toward the movement. The dataset only included tweets with the tag, #WomensMarch, so it's likely that not many tweets within the dataset obviously criticized the movement.

## Conclusion

### The Indian Farmers' Protest

Twitter notably had to jump hurdles with [the Indian government](https://www.npr.org/2021/02/17/968641246/twitter-in-standoff-with-indias-government-over-free-speech-and-local-law) about suppressing the backlash against the farm laws. Accounts were suspended at first and hashtags were reduced. As Twitter struggled between free speech and the government's orders, I wonder if this affected the results somehow.

<img width="600" alt="Indian Farmers' Protest Chart 1" src="Screenshot 2023-08-05 at 10.05.24 AM.png">
<img width="600" alt="Indian Farmers' Protest Chart 2" src="Screenshot 2023-08-05 at 10.04.43 AM.png">
<img width="600" alt="Indian Farmers' Protest Chart 3" src="Screenshot 2023-08-05 at 10.03.37 AM.png">
<img width="600" alt = "Indian Farmers' Protest Chart 4" src="Screenshot 2023-08-05 at 10.02.30 AM.png">

However, the public seems to be divided equally between negative, neutral, and positive reactions. The majority is overall neutral. The rest is more negatively positioned towards the movement, while the minority of tweets are positive. The traffic caused and the MP's smashed window seemed to have almost no change compared to the total sentiment. During the Republic's Day violence, though, the number of negative tweets drastically went up to almost 50% of the total number of tweets. Again, though, these results may not reflect the true sentiment towards the movement: the Indian government tried to suppress Twitter and shut down the internet in order to prevent support for the farmers. Also, this analysis doesn't exactly specify whether the negative tweets were directed towards the farmers or the government (it's likely that they were directed toward both).

### Women's March

The Women's March during its first protest seemed to be greatly supported. However, I think it would be an interesting project in the future to research how they are viewed today.

### As a whole...

Being inconvenienced actually didn't seem to affect the Indian farmers' movement at all. However, with more research, the results may turn out differently.

On the other hand, violence or unnecessarily brutal actions did seem to negatively impact a movement. [Research by a sociologist at Stanford](https://news.stanford.edu/2018/10/12/how-violent-protest-can-backfire/) has shown that violence from a popular movement will more negatively impact the movement compared to violence from the opposing side -- sometimes it will actually increase support for the opposing side.

I think most protesters who are 'disruptive' prefer the latter option. As one protester said, “It isn’t fun: I hate disrupting people’s lives, and it’s upsetting that it’s come to this. But it has come to this.”

***Notes:***
*This project is not verified or error-free. Please use results with caution. The Google Colab notebooks and HuggingFace/KeyBERT models used to create this research project are available for further analysis.*



