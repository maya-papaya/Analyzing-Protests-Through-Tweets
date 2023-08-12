# Analyzing Protests Through Tweets

In our modern society, protests are a way to collectively unite our voices to create change. However, some protests can negatively impact communities (looting, riots) or just be a nuisance (blocking traffic). Other times, people focus on the protesters' actions, rather than the message they're trying to spread (for example, the climate activists who threw soup at famous paintings). 

Still, experts say that [confrontational protests](https://grist.org/protest/confrontational-climate-protests-civil-disobedience-soup-van-gogh/) are an effective way to bring attention to a cause and portray less-bold protests in a better light. While this form of protest, called 'civil disobedience,' often is ineffective at garnering support for a movement, it has been a large part of effective social movements. Unfortunately for protestors, they have to choose between peaceful protests (usually ignored by the public) or civil disobedience (gaining the attention of the public and broadcasted by the media). The whole point of these confrontational protests *is* to make the public uncomfortable and force them into decisions. Social disruption has been a powerful tactic for very long: even suffragettes once slashed paintings and irreparably damaged them as a form of protest. Nowadays, civil disobedience is a tactic that has become increasingly popular among younger activists. A spokesperson from Just Stop Oil said, “We’re going to be noisy. We’re going to be disruptive. We’re going to be unignorable. We’re going to be a pain in the ass until you listen to us.”

However, the reality is that what constitutes an effective protest is a highly disputed topic. This is why I wanted to find out how we can effectively share our voices through protests and gain support without disrupting the cause.
This project is meant to explore public sentiment toward protests by analyzing tweets and what events can cause the public's attitude toward the movement to change.

I looked at two protests: the farmers' protest in India and the Women's March movement. Here's a little background on each:

### The Indian Farmers' Protest
The Indian farmers' protest lasted between 2020 and 2021. It was in response to laws passed by Prime Minister Narendra Modi which would minimize government involvement and instead encourage private investors. "More than 60 percent of India’s 1.3 billion people still depend primarily on agriculture for their livelihood, though the sector accounts for only about 15 percent of the country’s economic output," writes the New York Times, "For years, debts and bankruptcies have been driving farmers to high rates of suicide." Finally, the laws were repealed.

### Women's March
The Women's March movement began in 2017, the day after the inauguration of former President Donald Trump, due to his misogynistic rhetoric. It was recorded as the largest protest in U.S. history. Eventually, their mission adapted to include many issues - as the organization once said, "women's rights are human rights." Now, they have advocated on topics including "women's rights, immigration reform, healthcare reform, disability justice, reproductive rights, the environment, LGBTQ rights, racial equality, freedom of religion, workers' rights and tolerance," according to Wikipedia. To this day, they still arrange annual protests.

---

I divided my process into three parts: finding datasets, fine-tuning my model, and finally, conducting my analysis.

## Finding Datasets
I used a [HuggingFace dataset](https://huggingface.co/datasets/tweet_eval/viewer/sentiment/train) to train my model in sentiment analysis.

For the analysis, I chose two datasets from Kaggle ([Indian farmers' protest](https://www.kaggle.com/datasets/prathamsharma123/farmers-protest-tweets-dataset-csv) & [#WomensMarch movement](https://www.kaggle.com/datasets/adhok93/inauguration-and-womensmarch-tweets)).

## Fine-tuning the Model
I used finetuned my model to be a [sentiment analyzer](https://huggingface.co/mayapapaya/Sentiment-Analyzer).

## Conducting My Analysis
I had three functions:

* **Public Sentiment:** determines the majority sentiment towards the movement

* **Segmenting Dataset by Date (parameters: start_date, end_date):** segments a dataset within a specified time period.

* **Keyword Extractor:** finds all the most popular keywords within a dataset of tweets. For this function, I used a KeyBERT model to extract keywords.

Here are the results and conclusions I drew from my analysis:

---

## Results

### The Indian Farmers' Protest

The overall sentiment on Twitter towards the Indian farmers' protest is as shown:
```
Public Sentiment:

Positive Tweets: 193,742
Neutral Tweets: 504,129
Negative Tweets: 386,581

Total Tweets: 1,084,452
```
<img width="600" alt="Indian Farmers' Protest Chart 1" src="Screenshot 2023-08-05 at 10.05.24 AM.png">

The majority (about 40.7%) is unconcerned or neutral towards the Indian farmers' protests. About 34.9% are negatively geared toward it. The minority of tweets are supportive of the movement.
```
Keywords:
1. ('farmersprotest', 469192)
2. ('farmers', 84296)
3. ('farmers farmersprotest', 32333)
4. ('support farmers', 29321)
5. ('farmers protest', 20979)
6. ('protest', 20465)
7. ('bjp', 19193)
8. ('support farmersprotest', 17318)
9. ('farm laws', 15796)
10. ('indian farmers', 12893)
```
Two keywords, 'support farmers' and 'support farmersprotest,' indicate that the movement was greatly supported on social media. The high percentage of negative tweets was not necessarily directed toward the farmers -- those tweets may have been directed toward the government (Modi's Bharatiya Janata Party or B.J.P.) and the farm laws.
```
Wordcloud:
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers/Wordcloud.png">

Some words that stand out include 'support farmers,' 'human right,' 'support,' and 'shame.' Generally, it seems that the movement was greatly supported. Many of the negative tweets were likely directed toward the government.

---

For my second experiment, I decided to look at a specific instance where, on November 29th, "[the protesters announced that they would block five further points of entry into Delhi,](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" according to Wikipedia. Despite [overwhelming support for India's farmers](https://foreignpolicy.com/2021/11/28/farmers-protests-india-martyrs/), I was curious to see whether people would view this as a nuisance or support it.
```
Public Sentiment between 2021-11-05 00:00:00+00:00 and 2021-11-21 00:00:00+00:00: 

Positive Tweets: 5,098
Neutral Tweets: 11,037
Negative Tweets: 8,433

Total Tweets: 24,568
```
<img width="600" alt="Indian Farmers' Protest Chart 2" src="Screenshot 2023-08-05 at 10.04.43 AM.png">

The percentage of negative tweets decreases by 0.6%, while the percentage of positive tweets increases by 1%. There is almost no change between the total public sentiment and this instance.

---

I also thought that a certain instance where "a farmer's protest on 5 November turned violent and an MP's car window was smashed," according to Wikipedia, would be interesting to investigate.
```
Public Sentiment between 2021-11-05 00:00:00+00:00 and 2021-11-21 00:00:00+00:00: 

Positive Tweets: 5,098
Neutral Tweets: 11,037
Negative Tweets: 8,433

Total Tweets: 24,568
```
<img width="600" alt="Indian Farmers' Protest Chart 3" src="Screenshot 2023-08-05 at 10.03.37 AM.png">

This time, the percentage of negative tweets decreases by 1%, while the percentage of positive tweets increases by 3%. Since one smashed car window is more irrelevant to most people's lives and it's easier to distance one's self from that circumstance, it's possible that there was a less negative reception.

However, after further research, I found that the MP, Ram Chander Jangra, had incited several protests against himself because he called the farmers '[jobless alcoholics and bad elements.](https://thewire.in/agriculture/haryana-farmer-protests-jangra-car)' After this discovery, there is no doubt that Jangra reduced the possibility of sympathy from Twitter users.
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
There is no mention of any MP's car window being smashed. Likely, people did not care enough about Jangra's car and preferred to focus on the movement.
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
The phrase, 'farmlawsrepealed,' comes in third place. Another phrase, 'victory farmers,' likely celebrating the Indian farmers' victories and successful protests, also seems to be popular. This is likely because the farm laws would be scheduled to be repealed only a few days later.
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
The popularity of variations on 'farmlawsrepealed' and 'farm laws' can be attributed to how the farm laws would be repealed a few days later.
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
Again, there isn't much difference between negative keywords and the previously-discussed keywords. It seems, though, that this category of tweets is calling on Modi's Bharatiya Janata Party more frequently, no doubt to repeal the farm laws.
```
Wordcloud (Positive):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers 2/Positive.png">

In the positive wordcloud, there are words relating to victory ('victory,' 'finally,' 'proud,' 'won,' 'congratulation') and supportive words ('unity,' 'love,' 'live,' 'support,' 'fight'). This can be attributed to how the protests finally succeeded in repealing the farm laws.
```
Wordcloud (Neutral):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Neutral" src="/Farmers 2/Neutral.png">

The neutral wordcloud seems to have more words relating to the government and Modi ('narendramodi,' 'government' 'BJP,' 'PM Modi'), likely discussing their being about to repeal the farm laws.
```
Wordcloud (Negative):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Negative" src="/Farmers 2/Negative.png">

Some words that stand out include 'farmer,' 'narendramodi' (likely calling on Modi), 'government,' 'death' (possibly referring to the many deaths and suicides of farmers throughout the movement and in the past), 'shame,' and 'protest.' There still might be some resentment and anger against the government for their treatment of the farmers.

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

For this instance, the percentage of positive tweets dramatically decreases to 13%, while the percentage of negative tweets increases to almost 50%. These prominent changes may be because of the violence that occurred. Two major groups decided to leave the farmers' protest because of the violence and the Nishan Sahib, a Sikh religious flag. Likely, many people (including previous supporters of the movement) criticized the violence and the group of protesters who abandoned the original peaceful protest plan. Several protesters also resorted to vandalism. Over 300 police personnel and thousands of farmers were injured by the violence.

However, some of the negative tweets were likely directed towards the government, as well as their crackdown on the internet/social media.
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
Some keywords that became more popular include 'delhi police,' 'sikhs,' and 'flag.' These results make sense, considering that each of these keywords are related to the events of the Republic Day violence.

Interestingly enough, more people seemed to care about the violence that erupted between the farmers and the police, yet completely ignored an MP's window being smashed.
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
Some popular keywords used positively include 'peacefulprotestcontinues' and 'peace wins.' The likely explanation for their sudden usage may be to encourage more peaceful protests and attempt to reduce the backlash against the movement caused by the violence.
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
Some neutral keywords include 'tractor rally,' 'delhi police,' 'rakeshtikait farmersprotest,' and 'farmerprotest gazipurborder.' These tweets are likely from news outlets or reporters discussing the events that occurred during the Republic Day violence. 

Rakesh Tikait (from 'rakeshtikait farmersprotest') is a spokesperson of the Bharatiya Kisan Union, which notably withdrew from the protests after the violence. The Ghazipur border was a protest site for the farmers. [Tikait was reported to have broken down at the site](https://timesofindia.indiatimes.com/india/farmers-refuse-to-vacate-ghazipur-protest-site-singhu-turns-into-fortress-highlights/articleshow/80575153.cms), which may explain why both were mentioned more frequently.
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
The negative keywords topics do not differ much from the overall keywords. Sikhs and flag are frequently discussed, probably because of the anger at a religious flag being hoisted on top of the Red Fort during Republic Day. The phrase, 'protesting farmers,' is also mentioned frequently in the negative tweets, no doubt because of the violence and injuries that occurred.
```
Wordcloud (Positive):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers 2/Positive.png">

Some words that stand out include 'Republic Day,' 'Red Fort,' 'support farmers,' 'PeacefulProtestContinues,' 'Peace Wins,' and 'solidarity.'
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
Some of the most popularly used keywords include 'future female' and 'womensmarch power.' These results make sense, considering how supported the movement was.

The phrase, 'education devos,' refers to Betsy DeVos, who was nominated as Secretary of Education by the Trump admin. During her Senate confirmation hearing, she mentioned that guns were necessary in order to protect children from grizzly bears, causing many jokes to pop up around her and bears. Many people disapproved of her being nominated and questioned her competency. [Teachers participated in the Women's March](https://www.washingtonpost.com/local/education/teachers-to-march-against-trumps-education-agenda/2017/07/21/18a54c20-6e24-11e7-9c15-177740635e83_story.html) and targeted the Trump admin's choices relating to education.

Demi Lovato also [spoke at the march to about 750,000 people](https://www.justjaredjr.com/2017/01/21/demi-lovato-miley-cyrus-yara-shahidi-make-their-voices-heard-at-womens-march/), which explains her having being mentioned frequently.
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
Some of the positive keywords include shoutouts to public figures like Hillary Clinton (who ran against Trump in 2016) and Cecile Richards, [an activist who spoke at the march](https://19thnews.org/2021/10/i-need-to-be-with-other-folks-as-outraged-and-motivated-as-i-am-cecile-richards-on-why-this-years-womens-march-matters/#:~:text=In%202017%2C%20Cecile%20Richards%2C%20then,research%20and%20rapid%20response%20group.). Most of the positive tweets seem to be related to encouraging and praising the movement as well as its members.
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

An explanation for the Amy Mek reference may be because of her support of Donald Trump. *The New York Times* quoted her, "Amy Mek, who has more than 85,000 Twitter followers, is one of the women Ms. Suhler has gotten to know through their shared support of Mr. Trump. 'My belief has been that women’s rights is about treating men and women equally,' Ms. Mek said. 'Trump swings at men and women equally hard, but somehow if a woman is a Trump target, he is a misogynist.'" 

The phrases, 'sharia' and 'islam sharia,' refer to Shariah law. The Women's March in 2017 was wrapped up with conversations around Islam, including whether or not to [protest Shariah law.](https://torontosun.com/2017/01/26/farzana-hassan-when-will-womens-march-protest-sharia-law).
```
Wordcloud (Positive):
```
<img width="600" alt="Women's March Wordcloud Positive" src="/WomensMarch/Positive.png">

Some words that pop out include 'shoutout WomensMarch' and 'unstoppable.' Hillary Clinton and Cecile Richards seemed to be mentioned frequently. Demi Lovato and Miley Cyrus are also mentioned too, as well as Cyrus’s organization, the Happy Hippie Foundation.
```
Wordcloud (Neutral):
```
<img width="600" alt="Women's March Wordcloud Neutral" src="/WomensMarch/Neutral.png">

'Clinton says,' 'video statement,' 'WATCH,' and 'references' all suggest that the majority of neutral tweets were dedicated to sharing information on the events happening during the march.
```
Wordcloud (Negative):
```
<img width="600" alt="Women's March Wordcloud Negative" src="/WomensMarch/Negative.png">

'Genital mutilation' seems to be the most prominent discussion. 'Islam Sharia,' 'Amy Mek,' 'honor killings,' and 'Tahani Mansour' ([a woman who was killed by her father due to her dating a non-Muslim man and arriving home late](https://uncommongroundmedia.com/muslim-american-femicide-intersectional-feminist-enablers/?expand_article=1)) are all related to the conversation around Islam within the movement.

---

## Conclusion

### The Indian Farmers' Protest

Twitter notably had to jump hurdles with [the Indian government](https://www.npr.org/2021/02/17/968641246/twitter-in-standoff-with-indias-government-over-free-speech-and-local-law) about suppressing the backlash against the farm laws. Accounts were suspended at first and hashtags were reduced. As Twitter struggled between free speech and the government's orders, I wonder if this affected the results somehow.

The public seemed to be divided equally between negative, neutral, and positive reactions. The majority is overall neutral. While this seems strange, we can reason that the neutral tweets were dedicated to reporting on the events of the protests. The rest of the tweets is more negatively positioned towards the movement, while the minority of tweets are positive. The traffic caused and the MP's smashed window seemed to have almost no change compared to the total sentiment. During the Republic's Day violence, though, the number of negative tweets drastically went up to almost 50% of the total number of tweets. Again, though, these results may not reflect the true sentiment towards the movement: the Indian government tried to suppress Twitter and shut down the internet in order to prevent support for the farmers. However, because of the violence incited by some of the protesters, we can imagine that most of the negative tweets were directed toward them.

### Women's March

The Women's March, during its first protest, seemed to be greatly supported. However, I think it would be an interesting project in the future to research how they are viewed today. 

An explanation for the movement's widely-varying keywords may be because it was considered "[more than an anti-Trump protest,](https://www.vox.com/2017/1/21/14342942/womens-march-inauguration-trump-protest-goals-feminism-demands)" as *Vox* writes. The movement touched on many different conversations and issues considered especially vulnerable under the Trump administration, "[including women’s and reproductive rights, criminal justice, defense of the environment and the rights of immigrants, Muslims, LGBT people and the disabled.](https://www.history.com/this-day-in-history/womens-march)" This explains why conversations around Shariah law and Islam were so prevalent throughout the march.

### As a whole...

The majority sentiment of each dataset was neutral: this can attributed to the possibility that these tweets were reporting on the events of the protest. They were neither overtly supportive, nor critical of anyone; they were simply updates on how each movement was going. This hypothesis is supported by one of the neutral wordclouds, where phrases like 'video statement' and 'WATCH' were prevalent. 

Being inconvenienced actually didn't seem to affect the Indian farmers' movement and the Women's March at all. However, with more research and exploration of other movements, the results may turn out differently.

On the other hand, violence or unnecessarily brutal actions did seem to negatively impact a movement, as evidenced by the results from the Indian farmers' protest. [Research by a sociologist at Stanford](https://news.stanford.edu/2018/10/12/how-violent-protest-can-backfire/) has shown that violence from a popular movement will more negatively impact the movement compared to violence from the opposing side -- sometimes it will actually increase support for the opposing side.

But now, the question becomes: how long should it take for the authorities in our lives to make a change? How long should we protest quietly and peacefully with much detriment to many lives? How long will it take for people to pay attention and notice an important issue?

I think most protesters who are considered 'nonviolently disruptive' say no more. As one protester said, “It isn’t fun: I hate disrupting people’s lives, and it’s upsetting that it’s come to this. But it has come to this.”

***Notes:***
*This project is not verified or error-free. Please use results with caution. The Google Colab notebooks and HuggingFace/KeyBERT models used to create this research project are available for further analysis and inspection.*

*This project also does not express any political leanings; it is merely a datascience project conducted out of my personal interest.*

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

* Taylor, Adam. "Why is the world protesting so much? A new study claims to have some answers." *The Washington Post,* 4 Nov. 2021, www.washingtonpost.com/world/2021/11/04/protests-global-study/. Accessed 11 Aug. 2023.

* Brown, Emma. "Teachers to march against Trump’s education agenda." *The Washington Post,* 21 Jul. 2017, www.washingtonpost.com/local/education/teachers-to-march-against-trumps-education-agenda/2017/07/21/18a54c20-6e24-11e7-9c15-177740635e83_story.html. Accessed 12 Aug. 2023.


