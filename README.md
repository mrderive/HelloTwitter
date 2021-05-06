# HelloTwitter

A hello world implementation of a Twitter bot that monitors one account and sends an autoreply to every tweet and retweet.

## Installation

Install [jq](https://stedolan.github.io/jq/download/).
You should now have `/usr/bin/jq`.

Clone or download `urlencode` into your `/usr/local/bin` and give execute permissions:
```
sudo mv urlencode /usr/local/bin/urlencode
sudo chmod u+x /usr/local/bin/urlencode
```

Clone or download `hellotwitter` and give execute permissions:
```
sudo chmod u+x hellotwitter
```

## Configuration

Edit the `hellotwitter` script using `vim` or your preferred editor.

Fill in the username handle (without the "@") of the twitter account that you want to monitor, as well as the autoreply message:
```
# ============================================================================================================
# YOU need to fill out the target twitter account and your auto-reply message
target=''
message=''
```

Fill in all the oauth stuff:
```
# ============================================================================================================
# YOU need to fill this out using https://developer.twitter.com/en/portal/dashboard
oauth_bearer_token=''
oauth_consumer_key=''
oauth_consumer_secret=''
oauth_token=''
oauth_token_secret=''
```
If you do not know what this means, start with first creating a [developer account](https://developer.twitter.com/en/docs/developer-portal/overview). Then create a server side [app](https://developer.twitter.com/en/docs/apps/app-management). Then grant [Read and Write permissions](https://developer.twitter.com/en/docs/apps/app-permissions). Then generate all the oauth stuff. All of this should be done via the [Developer Portal](https://developer.twitter.com/en/portal/dashboard).

Seed a tweet ID into a file called `lastids.log`. For example:
```
echo 1362460946929696777 >>lastids.log
```
Note: This ID has to be within the last 7 days worth of ID's from the target account. The easiest way to get such an ID is to manually pull up the last tweet using your browser, copy the number part of the URL, and subtract 1.

## Usage

Just run the bash script:
```
./hellotwitter
```

If you want it to be a bot, then run it via a `cron` job.
