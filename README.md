# Analyzing Protests Through Tweets

In our modern society, protests are a way to collectively unite our voices to create change. However, some protests can negatively impact communities (looting, riots) or just be a nuisance (blocking traffic). Other times, people focus on the protesters' actions, rather than the message they're trying to spread (for example, the climate activists who threw soup at famous paintings). 

Still, experts say that [confrontational protests](https://grist.org/protest/confrontational-climate-protests-civil-disobedience-soup-van-gogh/) are an effective way to bring attention to a cause and portray less-bold protests in a better light. While this form of protest, called 'civil disobedience,' often is ineffective at garnering support for a movement, it has been a large part of effective social movements. Unfortunately for protestors, they have to choose between peaceful protests (usually ignored by the public) or civil disobedience (gaining the attention of the public and broadcasted by the media). The whole point of these confrontational protests *is* to make the public uncomfortable and force them into decisions. Social disruption has been a powerful tactic for very long: suffragettes once slashed paintings and went on hunger strikes to fight for their rights; Gandhi and his followers collected salt, defying the British East India Company's Salt Act. Nowadays, civil disobedience is a tactic that has become increasingly popular among younger activists. A spokesperson from Just Stop Oil said, “We’re going to be noisy. We’re going to be disruptive. We’re going to be unignorable. We’re going to be a pain in the ass until you listen to us.”

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

For my second function, I wanted to find four specific categories of instances: an example of civil disobedience (nonviolently disruptive and illegal), minor violence (minor and without casualties), a violent riot (violent with many casualties and damage), and a peaceful protest. I would then compare all these instances and see how public reactions changed for each one.

For civil disobedience, I decided to look at a specific instance where, on November 29th, "[the protesters announced that they would block five further points of entry into Delhi,](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" according to Wikipedia. Despite [overwhelming support for India's farmers](https://foreignpolicy.com/2021/11/28/farmers-protests-india-martyrs/), I was curious to see whether people would view this as a nuisance or support it.
```
Public Sentiment between 2020-11-29 00:00:00+00:00 and 2021-03-22 00:00:00+00:00: 

Positive Tweets: 116,545
Neutral Tweets: 283,172
Negative Tweets: 216,239

Total Tweets: 615,956
```
<img width="600" alt="Indian Farmers' Protest Chart 2" src="Screenshot 2023-08-05 at 10.04.43 AM.png">

The percentage of negative tweets decreases by 0.6%, while the percentage of positive tweets increases by 1%. There is almost no change between the total public sentiment and this instance.
```
Keywords:
1. ('farmersprotest', 254161)
2. ('farmers', 40145)
3. ('farmers farmersprotest', 16621)
4. ('support farmers', 14814)
5. ('rihanna', 12096)
6. ('protest', 11997)
7. ('farmers protest', 11825)
8. ('support farmersprotest', 10334)
9. ('bjp', 8947)
10. ('indian farmers', 8479)
```
No one mentioned how the entrances to Delhi were blocked. In fact, many people demonstrated their support for the farmers, with the phrase, ‘support farmers’ coming in fourth place. 

Rihanna is also mentioned frequently, likely because she had [posted a tweet supporting the movement](https://www.bbc.com/news/world-asia-india-55931894). Her tweet went viral, but there was much backlash from the Indian government and some pro-government public figures (one actress even called her a 'porn star') and criticism for involving herself in the protests.
```
Positive Keywords: 
1. ('farmersprotest', 66553)
2. ('farmers', 7400)
3. ('support farmers', 6318)
4. ('support farmersprotest', 5879)
5. ('rihanna', 5664)
6. ('farmers farmersprotest', 5638)
7. ('supporting farmersprotest', 2548)
8. ('farmersprotest istandwithfarmers', 2484)
9. ('gretathunberg', 2437)
10. ('supporting farmers', 2176)
```
Again, in the positive keywords, the support for the farmers is overwhelming. Rihanna is mentioned frequently once again.

Greta Thunberg, who had posted a toolkit of resources to effectively protest for the farmers, was also mentioned frequently. According to *The Times of India*, she was accused of being involved in a plot to defame India.
```
Neutral Keywords: 
1. ('farmersprotest', 130616)
2. ('farmers', 18327)
3. ('farmers farmersprotest', 8116)
4. ('farmers protest', 6617)
5. ('support farmers', 6421)
6. ('protest', 5222)
7. ('rihanna', 4375)
8. ('indian farmers', 4221)
9. ('stand farmers', 3801)
10. ('farm laws', 3456)
```
The neutral keywords also suggest that the movement was greatly supported. Rihanna’s support seems to have made an impact on the public.
```
Negative Keywords: 
1. ('farmersprotest', 56992)
2. ('farmers', 14418)
3. ('protest', 5995)
4. ('bjp', 5619)
5. ('farmers protest', 4321)
6. ('protesting', 3149)
7. ('farmers protesting', 3024)
8. ('farmers farmersprotest', 2867)
9. ('indianfarmershumanrights', 2795)
10. ('farmers india', 2338)
```
For the negative keywords, it is likely that the Twitter users are criticizing the government, especially considering the popularity of the phrase, ‘indianfarmershumanrights.’
```
Wordcloud (Positive):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Positive" src="/Farmers 1/Positive.png">

In the wordcloud, there are many words that suggest support for the movement (‘support,' love,' solidarity,' Thank,' supporting farmer’). Rihanna is also mentioned again, as well as Greta Thunberg.
```
Wordcloud (Neutral):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Neutral" src="/Farmers 1/Neutral.png">

The neutral wordcloud is more concerned with providing information and background on the movement, like describing the farm laws, referring to the government, mentioning Rihanna, etc. This output makes sense considering that this wordcloud covers tweets from the beginning of the movement when the public was learning what the movement was about.
```
Wordcloud (Negative):
```
<img width="600" alt="Indian Farmers' Protest Wordcloud Negative" src="/Farmers 1/Negative.png">

While most of the phrases relate to the farmers and the government, one word stood out to me -- ‘terrorist.’ After some research, I found that [the protesting farmers had been treated as terrorists](https://www.hindustantimes.com/india-news/shiv-sena-slams-bjp-calls-using-water-cannons-on-farmers-amid-cold-wave-cruel/story-swfrlF8AXq6S63uJ7HjAZP.html). So  we now know for sure that there was some pushback against the movement.

---

As an example of minor violence, I thought that a certain instance where "a farmer's protest on 5 November turned violent and an MP's car window was smashed," according to Wikipedia, would be interesting to investigate.
```
Public Sentiment between 2021-11-05 00:00:00+00:00 and 2021-11-21 00:00:00+00:00: 

Positive Tweets: 5,667
Neutral Tweets: 10,145
Negative Tweets: 8,756

Total Tweets: 24,568
```
<img width="600" alt="Indian Farmers' Protest Chart 3" src="Screenshot 2023-08-05 at 10.03.37 AM.png">

This time, the percentage of negative tweets decreases by 1%, while the percentage of positive tweets increases by 3%. Since one smashed car window is more irrelevant to most people's lives and it's easier to distance one's self from that circumstance, it's possible that there was a less negative reception.

However, after further research, I found that the MP, Ram Chander Jangra, had incited several protests against himself because he called the farmers '[jobless alcoholics and bad elements.](https://thewire.in/agriculture/haryana-farmer-protests-jangra-car)' After this discovery, there is no doubt that Jangra reduced the possibility of sympathy from Twitter users.
```
Keywords:
1. ('farmersprotest', 7274)
2. ('farmers', 2223)
3. ('farm laws', 1653)
4. ('farmlaws', 1597)
5. ('farmlawsrepealed', 1455)
6. ('farmersprotest twitter', 879)
7. ('farmlawsrepealed farmersprotest', 870)
8. ('farmlaws farmersprotest', 868)
9. ('farmersprotest farmlaws', 714)
10. ('farmersprotest farmlawsrepealed', 704)
```
There is no mention of any MP's car window being smashed. Likely, people did not care enough about Jangra's car and preferred to focus on the movement.
```
Positive Keywords: 
1. ('farmersprotest', 2303)
2. ('farmers', 577)
3. ('farmersprotest twitter', 360)
4. ('farmlawsrepealed', 323)
5. ('farmlaws', 297)
6. ('farmlawsrepealed farmersprotest', 222)
7. ('farm laws', 195)
8. ('farmlaws farmersprotest', 189)
9. ('farmersprotest farmlawsrepealed', 159)
10. ('farmers farmersprotest', 157)
```
The phrase, 'farmlawsrepealed,' comes in third place. Another phrase, 'victory farmers,' likely celebrating the Indian farmers' victories and successful protests, also seems to be popular. This is likely because the farm laws would be scheduled to be repealed only a few days later.
```
Neutral Keywords: 
1. ('farmersprotest', 3224)
2. ('farm laws', 855)
3. ('farmlaws', 852)
4. ('farmers', 709)
5. ('farmlawsrepealed', 692)
6. ('farmlaws farmersprotest', 451)
7. ('farmlawsrepealed farmersprotest', 390)
8. ('farmersprotest farmlaws', 369)
9. ('farmersprotest twitter', 356)
10. ('farmersprotest farmlawsrepealed', 298)
```
The popularity of variations on 'farmlawsrepealed' and 'farm laws' can be attributed to how the farm laws would be repealed a few days later.
```
Negative Keywords: 
1. ('farmersprotest', 1747)
2. ('farmers', 937)
3. ('farm laws', 603)
4. ('farmlaws', 448)
5. ('farmlawsrepealed', 440)
6. ('bjp', 394)
7. ('farmlawsrepealed farmersprotest', 258)
8. ('farmersprotest farmlawsrepealed', 247)
9. ('farmlaws farmersprotest', 228)
10. ('farmersprotest farmlaws', 192)
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

For a violent riot, I thought that the Republic Day violence could be an example. During that protest, "[the violence and hoisting of a religious flag on the ramparts of the Red Fort made the Bharatiya Kisan Union (Bhanu) and All India Kisan Sangharsh Co-ordination Committee decide to quit the farmers' protest.](https://en.wikipedia.org/wiki/2020–2021_Indian_farmers%27_protest#Blocking_of_borders_and_roads)" I wondered if that specific protest (combined with how "several metro stations were closed and mobile internet was suspended by police") affected the sentiment towards the protest.
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

As an example of a peaceful protest, I looked at an instance between November 26th and 28th, where the farmers held peaceful protests at Nirankari ground, [according to an article by *Indian Express*](https://indianexpress.com/article/india/one-year-of-farm-laws-timeline-7511961/).

---

### Women's March

For the first function, I found the following:
```
Public Sentiment between 2017-02-08 05:14:24 and 2017-02-07 04:09:25: 

Positive Tweets: 3747
Neutral Tweets: 7766
Negative Tweets: 3487

Total Tweets: 15000
```

<img width="600" alt="Women's March Protest Chart 1" src="Screenshot 2023-08-05 at 10.01.24 AM.png">

The overwhelming majority (about 81.4%) is either unconcerned or supportive of the Women's March movement. About 18.6% are negatively geared toward it. This result is unsurprising considering that this dataset only covers tweets from the first Women's March. However, since the movement's leaders became wrapped up in [several controversies](https://time.com/5505787/womens-march-washington-controversy/), I wonder how that number would change now.
```
Keywords:
1. ('womensmarch', 7314)
2. ('future female', 1777)
3. ('clinton says', 1675)
4. ('female references', 1671)
5. ('references womensmarch', 1670)
6. ('devos', 1501)
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
1. ('womensmarch', 2032)
2. ('unstoppable womensmarch', 641)
3. ('cecilerichards movement', 640)
4. ('movement unstoppable', 640)
5. ('womensmarch agree', 638)
6. ('shoutout womensmarch', 384)
7. ('hillaryclinton shoutout', 382)
8. ('thank hillaryclinton', 381)
9. ('womensmarch thank', 380)
10. ('patriotsparade liberal', 342)
```
Some of the positive keywords include shoutouts to public figures like Hillary Clinton (who ran against Trump in 2016) and Cecile Richards, [an activist who spoke at the march](https://19thnews.org/2021/10/i-need-to-be-with-other-folks-as-outraged-and-motivated-as-i-am-cecile-richards-on-why-this-years-womens-march-matters/#:~:text=In%202017%2C%20Cecile%20Richards%2C%20then,research%20and%20rapid%20response%20group.). Most of the positive tweets seem to be related to encouraging and praising the movement as well as its members.
```
Neutral Keywords: 
1. ('womensmarch', 4553)
2. ('future female', 1752)
3. ('clinton says', 1675)
4. ('female references', 1671)
5. ('references womensmarch', 1670)
6. ('devos', 1488)
7. ('womensmarch power', 1486)
8. ('education devos', 1485)
9. ('communities womensmarch', 1485)
10. ('demi', 849)
```
The neutral keywords seem to be related to the empowerment of women ('future female,' 'womensmarch power').
```
Negative Keywords: 
1. ('womensmarch', 729)
2. ('mutilation', 451)
3. ('genital mutilation', 450)
4. ('threat genital', 442)
5. ('state womensmarch', 442)
6. ('amymek washington', 441)
7. ('womensmarch nofascistusa', 407)
8. ('trumpprotest', 407)
9. ('antifa trumpprotest', 406)
10. ('impl0rable', 406)
```
The most popular negative keywords seem to be 'genital mutilation,' 'threat genital,' 'amymek,' 'sharia,' and 'war women.' 

An explanation for the Amy Mek reference may be because of her support of Donald Trump. *The New York Times* quoted her, "Amy Mek, who has more than 85,000 Twitter followers, is one of the women Ms. Suhler has gotten to know through their shared support of Mr. Trump. 'My belief has been that women’s rights is about treating men and women equally,' Ms. Mek said. 'Trump swings at men and women equally hard, but somehow if a woman is a Trump target, he is a misogynist.'" 

The phrases, 'sharia' and 'islam sharia,' refer to Shariah law. The Women's March in 2017 was wrapped up with conversations around Islam, including whether or not to [protest Shariah law.](https://torontosun.com/2017/01/26/farzana-hassan-when-will-womens-march-protest-sharia-law).

```
Hashtags:
1. letlizspeak
2. sallyyates
3. womensmarch
4. melissamccarthy
5. bansharia
6. hush
7. devos
8. theresistance
9. indivisible
10. nofascistusa
```


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

The public seemed to be divided equally between negative, neutral, and positive reactions. The majority is overall neutral. While this seems strange, we can reason that the neutral tweets were dedicated to reporting on the events of the protests. The rest of the tweets are more negatively positioned towards the movement, while the minority of tweets are positive. We know that there was pushback against the movement, as evidenced by one negative wordcloud. However, many of the negative tweets were likely also directed toward the government. 

The blocking of Delhi's entrances and the MP's smashed window seemed to have almost no change compared to the total sentiment. During the Republic's Day violence, though, the number of negative tweets drastically went up to almost 50% of the total number of tweets. Again, though, these results may not reflect the true sentiment towards the movement: the Indian government tried to suppress Twitter and shut down the internet in order to prevent support for the farmers. However, because of the violence incited by some of the protesters, we can imagine that most of the negative tweets were directed toward them.

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

* Grebbell, Caroline. "15 Examples of Civil Disobedience (Which Have Made a Difference)." *rebellion.global,* 03 Nov. 2020, rebellion.global/blog/2020/11/03/civil-disobedience-examples/. Accessed 12 Aug. 2023.

* Sharma, Deepali. "‘Farmers being treated as terrorists, attacked on Delhi borders’: Shiv Sena." *Hindustan Times,* 30 Nov. 2020, www.hindustantimes.com/india-news/shiv-sena-slams-bjp-calls-using-water-cannons-on-farmers-amid-cold-wave-cruel/story-swfrlF8AXq6S63uJ7HjAZP.html. Accessed 13 Aug. 2023.

* "Greta Thunberg tweets, deletes and then updates farm protest 'toolkit'." *The Times of India,* 4 Feb. 2021, timesofindia.indiatimes.com/india/greta-tweets-deletes-farmprotest-toolkit-creates-uproar/articleshow/80679959.cms?from=mdr. Accessed 13 Aug. 2023.

* Bozhinova, Katerina. Satre, Josh. Rajagopal, Shreyya. "An Unlikely Success: Demonstrations Against Farm Laws in India." *ACLED,* 17 Dec. 2021, acleddata.com/2021/12/17/an-unlikely-success-demonstrations-against-the-farm-laws-in-india/#:~:text=Despite%20high%2Dprofile%20incidents%20of,demonstrations%20have%20been%20largely%20peaceful.. Accessed 14 Aug. 2023.

* Nazir, Saddat. "The Indian Farmer Protests: A Rare Concession." *Harvard International Review,* 12 Jul. 2022, hir.harvard.edu/farmer-protests/#:~:text=Although%20beginning%20with%20peaceful%20rallies,and%20Haryana%2C%20demanding%20better%20conditions.. Accessed 14 Aug. 2023.


