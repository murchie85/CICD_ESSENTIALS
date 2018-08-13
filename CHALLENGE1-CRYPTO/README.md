# CRYPTOCURRENCY PROCESSING CHALLENGE


CHALLENGE1-CRYPTO | [CHALLENGE-2-TROLL_BOT](LAB2-TROLL/README.md) | [Home](../README.md) 

![alt text](https://news.yale.edu/sites/default/files/styles/featured_media/public/cryptocurrency-aleh-tsyvinski-ynews.jpeg?itok=3Wm2RTst&c=07307e7d6a991172b9f808eb83b18804)

# CHALLENGE GUIDELINES

Note this is not a lab, so there will not be step by step instructions rather a list of guidelines and target objectives to try and reach. Some key points to consider when working through this challenge 

* Improvise - my steps are just a set of guidelines, if you find a better way or another way that works for you then stick with that. 
* Try to keep this a learning process, rather than sticking to only the steps you know.
* Remember to make use of key learning resources such as [StackOverflow](https://stackoverflow.com/)
    
    

# CHALLENGE OUTLINE


The aim of this challenge is to make use of a cryptocurrency site, and utilize their metrics so that you can build your own reporting and alerting app. This will help you know when to buy and sell crypto currencies or at least keep on top of the action. 

![alt text](https://blog.digitexfutures.com/wp-content/uploads/2018/05/CoinMarketCap.png)

## OUTLINE 

1. FIRST have a look at [CoinMarketCap](https://coinmarketcap.com/) get a feel for what the site does.
2. **BONUS POINTS** if you can find documentation on their API, its important you have a look at this even if to get a feel for what it may/may not do.
3. Understand what JSON is, do not spend too much time on this but most APIs deal with passing information in JSON format, so its worth getting used to that format. Google sample JSON to have a look.
4. Work with the following URL to download data on all coins and their GBP values [CoinMarketCapAPI](https://api.coinmarketcap.com/v1/ticker/?convert=GBP) 
5. Build your first python job to pull that URL and convert to CSV. The easiest way to do this is to google for the answer, but the form should look something like the following:

'''

import urllib.request, json 
with urllib.request.urlopen("https://api.coinmarketcap.com/v1/ticker/?convert=GBP") as url:
    data = json.loads(url.read().decode())
    print(data)

'''
