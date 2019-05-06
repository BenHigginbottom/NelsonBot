# NelsonBot

Theres a joke going around on twitter spreading incorrect information about Lord Admiral Horatio Nelson (shocking I know), that is a mutation of the original joke here - https://twitter.com/kateejamieson/status/1002563139907485698

As Kate is THE authority on Nelson (we all have our 'things', hell I've just spent 20 mins dusting off this code), time for some mischief to prevent the spread!

Afterall, it is Nelson!


## Pre-requisites

Tested with Python 2.7, so this could be run on a Raspberry Pi 

Only external dependency is Tweepy, which assuming pip is installed, can be installed with the following command (Linux)

```bash
pip install tweepy --user
```

All testing has been conducted on Ubuntu Linux, although there isnt anything that would prevent it running on OSX or even Windows

## Setup

There are multiple tutorials on how to setup an app in twitter, so I'll just link to one -

https://dototot.com/how-to-write-a-twitter-bot-with-python-and-tweepy/

The application will need to be able to read and write to Twitter

## Configuration

With the Consumer and Access keys, the following section of the TwitterBot.py file will need to be updated

```python
CONSUMER_KEY = "CONSUMER_KEY"
CONSUMER_SECRET = "CONSUMER_SECRET"
ACCESS_TOKEN = "ACCESS_TOKEN"
ACCESS_TOKEN_SECRET = "ACCESS_TOKEN_SECRET"
```

We can then setup the search query to find the joke, like so

```python
query = "Lord Nelson AND 5ft tall AND statue AND 15ft AND Horatio AND 3:1"
```

And we now have the default responses to send for each of the search terms 

```python
rNelson = "He was 5ft 6 in real life and his statue is 17ft 4, but the Horatio is almost right. if you want to learn more about naval history - https://t.co/BeIDa0MkP7"
```

After this is the core logic, which "should not" need editing!

## Running

```bash
python ./NelsonBot.py
```

The program maintains a state in a textfile in the same directory as the program. This file contains the last ID of the tweet quoted and will only update the status if there is a new tweet.

There isnt a timer or other daemon yet, so the program will either need to be manually run or setup with a crontab

## To-do

* Convert into a lambda function (with a cloudwatch event trigger)
* State in dynamodb?