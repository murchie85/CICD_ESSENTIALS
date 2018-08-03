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