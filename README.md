# HelloTwitter

A hello world implementation of a Twitter bot that monitors one account and sends an autoreply to every tweet and retweet.

## Installation

Install [jq](https://stedolan.github.io/jq/download/).
You should now have `/usr/bin/jq`.

Install [GridSite](http://gridsite.org/wiki/Build_and_Install_Guide/). On Ubuntu (and probably on other Linux distros), there is already a precompiled package that can be installed by:
```
sudo apt-get install gridsite-clients
```
You should now have `/usr/bin/urlencode`.

Note: This package is probably overkill just to have the `urlencode` tool. You may instead just want to code your own bash function or copy it from a stackoverflow thread or something.

Clone or download `hellotwitter`.

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

Seed a tweet id into a file called `lastids.log`. For example:
```
echo 1362460946929696777 >>lastids.log
```
Note: This id has to be within the last 7 days worth of ids from the target account. The easiest way to get such an id is to manually pull up the last tweet using your browser, copy the number part of the URL, and subtract 1.

## Usage

Just run the bash script:
```
hellotwitter
```

If you want it to be a bot, then run it via a `cron` job.
