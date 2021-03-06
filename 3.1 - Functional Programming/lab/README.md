Fun with Toolz
----

For today's lab, I want you to familiarize yourself with the core `functools` library as well as the `toolz` library. One technique in particular I expect you to employ is [currying](http://toolz.readthedocs.io/en/latest/curry.html), though you need not use the `@curry` decorator, the [`partial`](https://docs.python.org/3/library/functools.html#functools.partial) function will suffice.

The goal of this lab is to extract the `expanded_url` strings from all `urls` in the `entities` object in each tweet.

For example:

    {
      ...
      "text": "Today, Twitter is updating embedded Tweets to enable a richer photo experience: https:\/\/t.co\/XdXRudPXH5",
      "entities": {
        "hashtags": [],
        "symbols": [],
        "urls": [{
          "url": "https:\/\/t.co\/XdXRudPXH5",
          "expanded_url": "https:\/\/blog.twitter.com\/2013\/rich-photo-experience-now-in-embedded-tweets-3",
          "display_url": "blog.twitter.com\/2013\/rich-phot\u2026",
          "indices": [80, 103]
        }],
        "user_mentions": []
      }
    }

has one object in the `urls` array containing the `"expanded_url": "https://blog.twitter.com/2013/rich-photo-experience-now-in-embedded-tweets-3"` (See the Twitter API documentation for [Entities](https://dev.twitter.com/overview/api/entities) for more details.)

You have been provided with a Python file, `get_urls.py`, which takes tweets as [`stdin`](https://en.wikipedia.org/wiki/Standard_streams#Standard_input_.28stdin.29). It iterates over each item returned by the `get_urls` function and prints it along with the tweet `id` (in a tab-delimited format).

Step 0: Set Up
------

1. `conda install toolz`
2. Download one of the files generated by Kinesis Firehose to test your script.

Step 1: Define `get_urls`
------

Your first step is to define the `get_urls` function according to functional principles. In order to demonstrate your understanding of `map` and `partial` your solution *must* use those two functions. (Hint: you will probably also want to use `get_in`.) You may *not* use `for` in this function.

Test your script with the following:

    cat <twitter-stream-data> | ./get_urls.py | head

You should get something like this:

    821220035540623360	None
    821219968456998914	http://ift.tt/2iGkb6P
    821219968456998914	http://ift.tt/2iGkb6P
    821220035544760320	http://fb.me/3e9zPxVVz
    821220073310474241	https://twitter.com/googuns_lulz/status/821220000631521280
    821220073310474241	https://twitter.com/5SOS/status/753850038707589120
    821220077496369152	https://curiouscat.me/mariajimenez/post/80730207?t=1484629098
    821220043925155842	http://dlvr.it/MnKpHH
    821220043925155842	None
    821220077500514304	https://twitter.com/dory/status/820818182231511040

Note that there are some `None`s even though this script will only print lines that have `urls`. This is because some `entities` may have url objects that are missing a value for `expanded_url`. These should be rare, however. (If most of your rows have `None` then you're probably doing something wrong.)

Minor stretch goal: filter out urls without an `expanded_url`.

Major stretch goal: refactor this code to use `pipe` _a la_ [Streaming Analytics](http://toolz.readthedocs.io/en/latest/streaming-analytics.html).
