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

* **Keyword Extractor (parameters: keywords):** determines whether the issue itself is being spread, or whether the protester’s actions distract from that. I had a list, *keywords*, that held all the keyword variations that are related to a protest rather than the movement itself (e.g., keywords like "riot", "nuisance", "traffic", "problem", etc.). For this function, I used a KeyBERT model to extract keywords.

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
Public Sentiment between 2021-11-05 00:00:00+00:00 and 2021-11-21 00:00:00+00:00: 

Positive Tweets: 5098
Neutral Tweets: 11037
Negative Tweets: 8433

Total Tweets: 24568
```
<img width="600" alt="Indian Farmers' Protest Chart 2" src="Screenshot 2023-08-05 at 10.04.43 AM.png">

The percentage of negative tweets decreases by 0.6%, while the percentage of positive tweets increases by 1%. There is almost no change between the total public sentiment and this instance.

---

I also thought that a certain instance where "a farmer's protest on 5 November turned violent and a MP's car window was smashed," according to Wikipedia, would be interesting to investigate.
```
Public Sentiment between 2021-11-05 00:00:00+00:00 and 2021-11-21 00:00:00+00:00: 

Positive Tweets: 5,098
Neutral Tweets: 11,037
Negative Tweets: 8,433

Total Tweets: 24,568
```
<img width="600" alt="Indian Farmers' Protest Chart 3" src="Screenshot 2023-08-05 at 10.03.37 AM.png">

This time, the percentage of negative tweets decreases by 1%, while the percentage of positive tweets increases by 3%. Since one smashed car window is more irrelevant to most people's lives and it's easier to distance one's self from that circumstance, it's possible that there was a less negative reception.
```
Keywords:
1. ('farmersprotest', 9343)
2. ('farmers', 1907)
3. ('farmlaws', 1760)
4. ('farmlawsrepealed', 1751)
5. ('farm laws', 1518)
6. ('farmlaws farmersprotest', 1123)
7. ('farmlawsrepealed farmersprotest', 1051)
8. ('farmersprotest farmlaws', 899)
9. ('farmersprotest farmlawsrepealed', 882)
10. ('bjp', 605)
```
The most popular keywords seem to be 'farmlaws' and 'farmlawsrepealed,' both likely hashtags. There seem to be a lot more emphasis on the farmers rather than just the farm laws themselves. 
```
Positive Keywords: 
1. ('farmersprotest', 2623)
2. ('farmers', 456)
3. ('farmlawsrepealed', 317)
4. ('farmlaws', 291)
5. ('farmers farmersprotest', 213)
6. ('farmlawsrepealed farmersprotest', 195)
7. ('farmlaws farmersprotest', 191)
8. ('farmersprotest farmlawsrepealed', 186)
9. ('farmersprotest farmlaws', 172)
10. ('victory farmers', 140)
```
Again, 'farmlawsrepealed' comes in at third place. 'Victory farmers,' likely celebrating the Indian farmers' victories and successful protests, also seems to be popular.
```
Neutral Keywords: 
1. ('farmersprotest', 4551)
2. ('farmlaws', 976)
3. ('farmlawsrepealed', 927)
4. ('farm laws', 907)
5. ('farmers', 661)
6. ('farmlaws farmersprotest', 650)
7. ('farmlawsrepealed farmersprotest', 546)
8. ('farmersprotest farmlaws', 480)
9. ('farmersprotest farmlawsrepealed', 410)
10. ('repeal farm', 301)
```
There isn't a major difference between the positive keywords and neutral keywords, except for a less celebratory mood (no 'victory farmers'). These keywords seem to be more interested in targeting the cause rather than being explicitly supportive.
```
Negative Keywords: 
1. ('farmersprotest', 2169)
2. ('farmers', 790)
3. ('farm laws', 510)
4. ('farmlawsrepealed', 507)
5. ('farmlaws', 493)
6. ('bjp', 369)
7. ('farmlawsrepealed farmersprotest', 310)
8. ('farmersprotest farmlawsrepealed', 286)
9. ('farmlaws farmersprotest', 282)
10. ('farmersprotest farmlaws', 247)
```
Again, there isn't much difference between the different sentiment categories of keywords. It seems, though, that this category of tweets is calling on Modi'sBharatiya Janata Party (B.J.P.).

```
Wordcloud (Positive):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers 2/Positive.png">

In the wordcloud, there are words relating to victory ('victory,' 'finally,' 'proud,' 'won,' 'congratulation') and supportive words ('unity,' 'love,' 'live,' 'support,' 'fight').
```
Wordcloud (Neutral):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Neutral" src="/Farmers 2/Neutral.png">

The neutral wordcloud seems to have more words relating to the government and Modi ('narendramodi,' 'government' 'BJP,' 'PM Modi').
```
Wordcloud (Negative):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Negative" src="/Farmers 2/Negative.png">

Some words that stand out include 'farmer,' 'narendramodi' (likely calling on Modi), 'government,' 'death' (possibly referring to the many deaths and suicides of farmers throughout the movement and in the past), 'shame,' and 'protest.'

---

During the Republic Day protest, "[the violence and hoisting of a religious flag on the ramparts of the Red Fort made the Bharatiya Kisan Union (Bhanu) and All India Kisan Sangharsh Co-ordination Committee decide to quit the farmers' protest.](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" I wondered if that specific protest (combined with how "several metro stations were closed and mobile internet was suspended by police") affected the sentiment towards the protest.
```
Public Sentiment between 2021-01-26 00:00:00+00:00 and 2021-02-01 00:00:00+00:00: 

Positive Tweets: 3,423
Neutral Tweets: 16,379
Negative Tweets: 18,936

Total Tweets: 38,738
```
<img width="600" alt = "Indian Farmers' Protest Chart 4" src="Screenshot 2023-08-05 at 10.02.30 AM.png">

For this instance, the percentage of positive tweets dramatically decreases to 13%, while the percentage of negative tweets increases to almost 50%. These prominent changes may be because of the violence that occurred. Two major groups decided to leave the farmers' protest because of the violence and religious flag. Likely, many people (including previous supporters of the movement) criticized the violence and the group of protesters who abandoned the original peaceful protest plan. Another factor contributing to the lack of positive support is the internet shutdown that caused farmers to lose contact with their supporters.

However, some of the negative tweets were likely also directed towards the government and their treatment of the farmers, as well as their crackdown on the internet/social media.
```
Keywords:
1. ('farmersprotest', 12696)
2. ('farmers', 1705)
3. ('protest', 1331)
4. ('farmers protest', 1001)
5. ('delhi police', 776)
6. ('farmersprostests farmersprotest', 661)
7. ('sikhs', 559)
8. ('farmers farmersprotest', 542)
9. ('flag', 525)
10. ('bjp', 499)
```
Some keywords that became more popular include 'delhi police,' 'sikhs,' and 'flag.' These results make sense, considering that each of these keywords are related to the events of the Republic's Day violence.
```
Positive Keywords: 
1. ('farmersprotest', 1430)
2. ('republic day', 187)
3. ('farmers', 163)
4. ('support farmers', 122)
5. ('peacefulprotestcontinues farmersprotest', 111)
6. ('farmers farmersprotest', 85)
7. ('farmersstandingfirm', 84)
8. ('support farmersprotest', 82)
9. ('republic', 80)
10. ('peace wins', 73)
```
Some popular keywords used positively include 'peacefulprotestcontinues' and 'peace wins.' The likely explanation for their sudden usage may be to reduce the backlash against the Indian farmers' protests due to the Republic's Day violence.
```
Neutral Keywords: 
1. ('farmersprotest', 6634)
2. ('farmers', 600)
3. ('farmers protest', 561)
4. ('protest', 554)
5. ('tractor rally', 344)
6. ('rakeshtikait farmersprotest', 318)
7. ('farmerprotest', 304)
8. ('farmersprotest farmerprotest', 302)
9. ('delhi police', 288)
10. ('farmerprotest gazipurborder', 277)
```
Some neutral keywords include 'tractor rally,' 'delhi police,' 'rakeshtikait farmersprotest,' and 'farmerprotest gazipurborder.' These tweets are likely news outlets or reporters discussing the events that occurred during the Republic's Day violence. Rakesh Tikait (from rakeshtikait farmersprotest') is a spokesperson of the Bharatiya Kisan Union which notably withdrew from the protests after the violence.
```
Negative Keywords: 
1. ('farmersprotest', 4632)
2. ('farmers', 942)
3. ('protest', 749)
4. ('delhi police', 470)
5. ('farmers protest', 412)
6. ('farmersprostests farmersprotest', 375)
7. ('bjp', 355)
8. ('sikhs', 340)
9. ('flag', 331)
10. ('protesting farmers', 323)
```
The negative keywords topics do not differ much from the overall keywords.
```
Wordcloud (Positive):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers 2/Positive.png">

Some notable words include 'Republic Day,' 'Red Fort,' 'support farmers,' 'PeacefulProtestContinues,' 'Peace Wins,' and 'solidarity.'
```
Wordcloud (Neutral):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Neutral" src="/Farmers 2/Neutral.png">

Most of the words in the neutral wordcloud refer to the events of the day ('Republic Day,' 'violence,' 'Delhi Police,' 'Sikh,' 'Tractor Rally').
```
Wordcloud (Negative):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Negative" src="/Farmers 2/Negative.png">

Some major words include 'Delhi,' 'police,' 'shame,' and 'violence.'

---

### Women's March

For the first function, I found the following:
```
Public Sentiment between 2017-02-08 05:14:24 and 2017-02-07 04:09:25: 

Positive Tweets: 3,034
Neutral Tweets: 9,209
Negative Tweets: 2,757

Total Tweets: 15,000
```
<img width="600" alt="Women's March Protest Chart 1" src="Screenshot 2023-08-05 at 10.01.24 AM.png">

The overwhelming majority (about 81.4%) is either unconcerned or supportive of the Women's March movement. About 18.6% are negatively geared toward it. This result is unsurprising considering that this dataset only covers tweets from the first Women's March. However, since the movement's leaders became wrapped up in [several controversies](https://time.com/5505787/womens-march-washington-controversy/), I wonder how that number would change now.
```
Keywords:
1. ('womensmarch', 6393)
2. ('rt womensmarch', 2644)
3. ('future female', 1781)
4. ('female references', 1671)
5. ('references womensmarch', 1670)
6. ('womensmarch htt', 1654)
7. ('education devos', 1489)
8. ('communities womensmarch', 1488)
9. ('womensmarch power', 1486)
10. ('demi lovato', 944)
```
Some of the most popularly used keywords include 'future female' and 'womensmarch power.' These results make sense considering how supported the movement was.
```
Positive Keywords: 
1. ('womensmarch', 1534)
2. ('rt womensmarch', 1020)
3. ('unstoppable womensmarch', 641)
4. ('womensmarch rt', 640)
5. ('cecilerichards movement', 640)
6. ('shoutout womensmarch', 384)
7. ('hillaryclinton shoutout', 381)
8. ('womensmarch thank', 380)
9. ('womens march', 167)
10. ('womensmarch womensmarch', 140)
```
Some of the positive keywords include shoutouts to public figures like Hillary Clinton (who ran against Trump in 2016) and Cecile Richards ([an activist who spoke at the march](https://19thnews.org/2021/10/i-need-to-be-with-other-folks-as-outraged-and-motivated-as-i-am-cecile-richards-on-why-this-years-womens-march-matters/#:~:text=In%202017%2C%20Cecile%20Richards%2C%20then,research%20and%20rapid%20response%20group.). Most of the positive tweets seem to be related to encouraging and praising the movement as well as its members.
```
Neutral Keywords: 
1. ('womensmarch', 4313)
2. ('future female', 1751)
3. ('female references', 1671)
4. ('references womensmarch', 1670)
5. ('womensmarch htt', 1654)
6. ('rt womensmarch', 1581)
7. ('womensmarch power', 1486)
8. ('communities womensmarch', 1485)
9. ('education devos', 1485)
10. ('demi', 839)
```
The neutral keywords seem to be related to the empowerment of women ('future female,' 'womensmarch power').
```
Negative Keywords: 
1. ('womensmarch', 546)
2. ('genital mutilation', 450)
3. ('threat genital', 442)
4. ('amymek washington', 441)
5. ('rt amymek', 441)
6. ('amymek', 441)
7. ('sharia', 164)
8. ('islam sharia', 125)
9. ('war women', 124)
10. ('sandratxas islam', 122)
```
The most popular negative keywords seem to be 'genital mutilation,' 'threat genital,' 'amymek,' 'sharia,' and 'war women.' 

The phrases, 'sharia' and 'islam sharia,' refer to Shariah law. The Women's March in 2017 was wrapped up with conversations around Islam, including whether or not to [protest Shariah law.](https://torontosun.com/2017/01/26/farzana-hassan-when-will-womens-march-protest-sharia-law).

An explanation for the Amy Mek reference may be because of her support of Donald Trump. *The New York Times* quoted her, "Amy Mek, who has more than 85,000 Twitter followers, is one of the women Ms. Suhler has gotten to know through their shared support of Mr. Trump. 'My belief has been that women’s rights is about treating men and women equally,' Ms. Mek said. 'Trump swings at men and women equally hard, but somehow if a woman is a Trump target, he is a misogynist.'" 

```
Wordcloud (Positive):
```
<img width="600" alt="Women's March Wordcloud Positive" src="/WomensMarch/Positive.png">

Some words that pop out include 'shoutout WomensMarch' and 'unstoppable.' Hillary Clinton and Cecile Richards seemed to be mentioned frequently.
```
Wordcloud (Neutral):
```
<img width="600" alt="Women's March Wordcloud Neutral" src="/WomensMarch/Neutral.png">

'Clinton says,' 'video statement,' 'WATCH,' and 'references' all suggest that the majority of neutral tweets was sharing information on the events happening during the march.
```
Wordcloud (Negative):
```
<img width="600" alt="Women's March Wordcloud Negative" src="/WomensMarch/Negative.png">

'Genital mutilation' seems to be the most prominent discussion. 'Islam Sharia,' 'Amy Mek,' 'honor killings,' and 'Tahani Mansour' ([a woman who was killed by her father due to her dating a non-Muslim man and arriving home late](https://uncommongroundmedia.com/muslim-american-femicide-intersectional-feminist-enablers/?expand_article=1)) are all related to the conversation around Islam within the movement.

---

## Conclusion

### The Indian Farmers' Protest

Twitter notably had to jump hurdles with [the Indian government](https://www.npr.org/2021/02/17/968641246/twitter-in-standoff-with-indias-government-over-free-speech-and-local-law) about suppressing the backlash against the farm laws. Accounts were suspended at first and hashtags were reduced. As Twitter struggled between free speech and the government's orders, I wonder if this affected the results somehow.

However, the public seems to be divided equally between negative, neutral, and positive reactions. The majority is overall neutral. The rest is more negatively positioned towards the movement, while the minority of tweets are positive. The traffic caused and the MP's smashed window seemed to have almost no change compared to the total sentiment. During the Republic's Day violence, though, the number of negative tweets drastically went up to almost 50% of the total number of tweets. Again, though, these results may not reflect the true sentiment towards the movement: the Indian government tried to suppress Twitter and shut down the internet in order to prevent support for the farmers. Also, this analysis doesn't exactly specify whether the negative tweets were directed towards the farmers or the government (it's likely that they were directed toward both).

### Women's March

The Women's March during its first protest seemed to be greatly supported. However, I think it would be an interesting project in the future to research how they are viewed today. An explanation for its widely-varying keywords may be because it was "[more than an anti-Trump protest,](https://www.vox.com/2017/1/21/14342942/womens-march-inauguration-trump-protest-goals-feminism-demands)" as *Vox* writes. The movement touched on many different conversations and issues.

### As a whole...

Being inconvenienced actually didn't seem to affect the Indian farmers' movement at all. However, with more research, the results may turn out differently.

On the other hand, violence or unnecessarily brutal actions did seem to negatively impact a movement. [Research by a sociologist at Stanford](https://news.stanford.edu/2018/10/12/how-violent-protest-can-backfire/) has shown that violence from a popular movement will more negatively impact the movement compared to violence from the opposing side -- sometimes it will actually increase support for the opposing side.

I think most protesters who are 'disruptive' prefer the latter option. As one protester said, “It isn’t fun: I hate disrupting people’s lives, and it’s upsetting that it’s come to this. But it has come to this.”

***Notes:***
*This project is not verified or error-free. Please use results with caution. The Google Colab notebooks and HuggingFace/KeyBERT models used to create this research project are available for further analysis.*

---

## References

* Leow, Griffin. "Analysis of Tweets on the Hong Kong Protest Movement 2019 with Python." *Towards Data Science,* 18 Nov. 2019, towardsdatascience.com/analysis-of-tweets-on-the-hong-kong-protest-movement-2019-with-python-a331851f061. Accessed 8 Aug. 2023.

* De Witte, Melissa. "How violent protest can backfire." *Stanford News,* 12 Oct. 2018, news.stanford.edu/2018/10/12/how-violent-protest-can-backfire/. Accessed 8 Aug. 2023.

* Yoder, Kate. "Climate activists’ new, confrontational tactics aren’t popular. That’s kind of the point." *Grist,* 21 Dec. 2022, grist.org/protest/confrontational-climate-protests-civil-disobedience-soup-van-gogh/. Accessed 8 Aug. 2023.

* Mir, Shoaib. Khan, Ahmer. "Farmers Have Become Martyrs in India." *Foreign Policy,* 28 Nov. 2021, foreignpolicy.com/2021/11/28/farmers-protests-india-martyrs/. Accessed 8 Aug. 2023.

* "2020–2021 Indian farmers' protest." *Wikipedia,* en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest. Accessed 8 Aug. 2023.

* Vesoulis, Abby. "Women First Marched to Challenge Trump. Now They Are Challenging Each Other." *Time,* 19 Jan. 2019, time.com/5505787/womens-march-washington-controversy/. Accessed 8 Aug. 2023.

* Frayer, Lauren. Bond, Shannon. "Twitter In Standoff With India's Government Over Free Speech And Local Law." *NPR,* 18 Feb. 2021, www.npr.org/2021/02/17/968641246/twitter-in-standoff-with-indias-government-over-free-speech-and-local-law. Accessed 8 Aug. 2023.

* Roller, Emma. "The Women Who Like Donald Trump." *The New York Times,* 10 May, 2016, www.nytimes.com/2016/05/10/opinion/campaign-stops/the-women-who-like-donald-trump.html. Accessed 10 Aug. 2023.


