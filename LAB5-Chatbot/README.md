# LETS BUILD A SIMPLE PYTHON CHATBOT


Chatbots are the new core of modern day sophisticated apps that require front end customer interaction. In this lab we will look at building our own simple non-intelligent app, but show how intelligence can be added or faked using a few simple tricks such as regex expressions. We will then build a more sophisticated app that we can deploy to facebook
Agenda:

* Python Chatbot Basics
* RegEx expressiosn 
* Hosting an intelligent chatbot on the cloud and deploying to facebook.

![alt text](https://securecdn.pymnts.com/wp-content/uploads/2017/03/chatbot.png)


# Getting Setup

First things first, lets install python for windows, and learn how to work with dependencies. 

* Install python from [Python Download](https://www.python.org/downloads/windows/)
* Run a sample Hello world program

1. Once you have installed Python3, open notepad++ and create a file called helloword.py (create a new folder called chatbot) 
2. In the file paste the following code  
``` print("hello World") ```
3. now from command line, gitbash or terminal, navigate to this folder where the file is stored and run the following   
``` python3 helloworld.py ```



# Understanding functions 

A function is something you call, that does a job and passes back a response that you can work with. A simple function that takes whatever you enter, and prints it out is this one:


```
def printmessage(message):
    print(message)
    return 


printmessage("hi")

```

* def means deine a function, it has to have the format def functionname(somethingthatgetspassedin)
* inside the function you can do whatever you want, for example we print the message that  gets passed in
* we write return, but we don't return anything. So this function just prints the message that gets passed in.

The part where we define the function does not get executed by the compiler, until it reaches the line *printmessage* only when it reaches that line, it calls the function and passes in 'hi' 


## Returning a value
```

def anothernewfunction(value):
    total = value + 10


    return total



anothernewfunction(22)

```
 

So in this case, when anothernewfunction is called, it passes in 22, then the total variable adds 10 to it. 



# Python Chatbot 

Below is the bare bones, but lots of new concepts here I will talk through as we work through them. 

```
bot_template = "BOT : {0}"
user_template = "USER : {0}"

# Define a function that responds to a user's message: respond

def respond(message):
    
    # Concatenate the user's message to the end of a standard bot respone
    bot_message = "I can hear you! You said: " + message
    
    return bot_message  # Return the result

# Define a function that sends a message to the bot: send_message
def send_message(message):
    
    # Print user_template including the user_message
    print(user_template.format(message))

    
    response = respond(message) # Get the bot's response to the message
    
    print(bot_template.format(response)) # Print the bot template including the bot's response.

# Send a message to the bot
send_message("hello")

```


## Adding complexity - full ask/answer chatbot


```

# Import the random module
import random

# This is a clever python trick, 
bot_template = "BOT : {0}"
user_template = "USER : {0}"



name = "Skitter Face"
weather = "cloudy"





responses = {
  "what's your name?": [
      "my name is {0}".format(name), #note the {0} pulls in the variable linked
      "they call me {0}".format(name),
      "I go by {0}".format(name)
   ],
    
    
  "what's today's weather?": [
      "the weather is {0}".format(weather),
      "it's {0} today".format(weather)
    ],
    
    
  "default": ["Here is a default message ya bam", "Does not compute", "whit?"]
}





# Use random.choice() to choose a matching response
def respond(message):
    # Check if the message is in the responses
    if message in responses:
        # Return a random matching response
        bot_message = random.choice(responses[message])
    else:
        # Return a random "default" response
        bot_message = random.choice(responses["default"])
    return bot_message



def send_message(message):
    
    # Print user_template including the user_message
    print(user_template.format(message))

    
    response = respond(message) # Get the bot's response to the message
    
    print(bot_template.format(response)) # Print the bot template including the bot's response.
    


send_message("what's your name?")
send_message("what's today's weather?")
insend_message("Hi")

```

## LETTING THE USER ASK 


Now we will take away the automated responses and give the user the chance to ask himself:

First delete these lines 
```

send_message("what's your name?")
send_message("what's today's weather?")
insend_message("Hi")


```

And replaces with the following lines 

```

toSend = input()
send_message(toSend)

```
This basically means if we type it in exactly, the bot will respond how we want it too.


## Abstracting a Response 

This time we will try to make a generic bot that is still useless but fakes a bit of intelligence, basically we will check for a ? mark and if it is there, we will answer the question vaguely, if not we will add an affirmative response. 

```

import random

bot_template = "BOT : {0}"
user_template = "USER : {0}"

responses = {'question': ["I don't know :(", 'you tell me!'],
 'statement': ['tell me more!',
  'why do you think that?',
  'how long have you felt this way?',
  'I find that extremely interesting',
  'can you back that up?',
  'oh wow!',
  ':)']}



# Define a function that sends a message to the bot: send_message
def send_message(message):
    # Print user_template including the user_message
    print(user_template.format(message))
    # Get the bot's response to the message
    response = respond(message)
    # Print the bot template including the bot's response.
    print(bot_template.format(response))

def respond(message):
    # Check for a question mark
    if message.endswith("?"):
        # Return a random question
        return random.choice(responses["question"])
    # Return a random statement
    return random.choice(responses["statement"])





# Send messages ending in a question mark
send_message("what's today's weather?")


# Send messages which don't end with a question mark
send_message("I love building chatbots")



```


# REGEX Expressions 

Getting used to coding REGEX expressions are extremely useful, because they allow you to work with fields that aren't exact, account for typos and spot patterns. 

```

import re
import random


user_template = 'USER : {0}'
bot_template = 'BOT : {0}'

keywords = {'goodbye': ['bye', 'farewell'],
 'greet': ['hello', 'hi', 'hey'],
 'thankyou': ['thank', 'thx']}
responses = {'default': 'default message',
 'goodbye': 'goodbye for now',
 'greet': 'Hello you! :)',
 'thankyou': 'you are very welcome'}


def send_message(message):
    print(user_template.format(message))
    response = respond(message)
    print(bot_template.format(response))


# Define find_name()
def find_name(message):
    name = None
    # Create a pattern for checking if the keywords occur
    name_keyword = re.compile('name|call')
    # Create a pattern for finding capitalized words
    name_pattern = re.compile('[A-Z]{1}[a-z]*')
    if name_keyword.search(message):
        # Get the matching words in the string
        name_words = name_pattern.findall(message)
        if len(name_words) > 0:
            # Return the name if the keywords are present
            name = ' '.join(name_words)
    return name

# Define respond()
def respond(message):
    # Find the name
    name = find_name(message)
    if name is None:
        return "Hi there!"
    else:
        return "Hello, {0}!".format(name)

# Send messages
send_message("my name is David Copperfield")
send_message("call me Ishmael")
send_message("People call me Cassandra")

```




# BUILD, CUSOMISE AND DEPLOY A SMARTBOT ON THE CLOUD AND FACEBOOK

![API.AI](https://cdn0.tnwcdn.com/wp-content/blogs.dir/1/files/2014/09/apiai-730x283.jpg)  


In this tutorial we will work through the example in googles engine, API.AI , it is really powerful and does all the hard stuff for us. 

We will follow all the tutorial steps in the following link, its pretty simple to use : [API.AI](https://dialogflow.com/)