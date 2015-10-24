---
layout: post
title: "@metricbot"
---

In January 2011, my friend [John](http://www.johnkaberg.se) sent me a chat
message asking if I knew what it
takes to make a Twitter bot. I confessed that I didn't know the specifics, but
that I supposed it couldn't be too tricky. He explained his idea to me: a bot
that would teach Americans to use metric units. It would find tweets using
imperial units and kindly point out that they could use the equivalent in
metric.

By the time, I hadn't done any programming on the web so learning the Twitter
API and a suitable programming language seemed like a hurdle too high. However,
we knew of [Twitterfeed](http://twitterfeed.com/) so we thought if we could just
construct a feed with the tweets we wanted to send we would be able to use that
service to put them on Twitter.

At this point, John introduced me to
[Yahoo! Pipes](https://en.wikipedia.org/wiki/Yahoo!_Pipes) - a visual editor for
feed remixing. Pipes has since been shut down by Yahoo!, presumably because the
number of users willing to learn programming without learning a real language
is limited.

Pipes had some really powerful features, including regular expressions.
My solution was basically to use the search feed for "inch" as my source and
then run a regular expression looking for numbers followed by the unit. I could
then pull the number and convert it to metric equivalent. After that it was just
a matter of assembling a suitable response and piping it to the output feed.
Pipes could accept GET parameters so I reused the same pipe for a few other
units including miles and yards.

John set up Twitterfeed and registered the handle @metricbot. We collectively
decided on the name and bio. We chose to name the bot A-L Lavoisier after
[Antoine-Laurent de Lavoisier](https://en.wikipedia.org/wiki/Antoine_Lavoisier),
one of the founders of the metric system. In the bio, we referenced the loss of
the [Mars Climate Orbiter](https://en.wikipedia.org/wiki/Mars_Climate_Orbiter)
in 1999 due to one piece of software talking in US customary units and another
piece of software expecting those results to be in metric units.

There was one obvious limitation with our implementation, namely that both
Pipes and Twitterfeed had rate limitations which meant we could only send a
handful of responses once in a while. This turned out to work in favour of the
bot since it would probably have been banned for spamming much earlier had it
not been limited in this way.

Our bot ended up running from 15 January 2011 to
2 May 2011 when it was suspended.During those months, we managed to
[upset](https://twitter.com/search?q=%40metricbot&src=typd)
a large number of Americans (especially Texans) and a few occasional Brits.

<div class="storify"><iframe src="http://storify.com/belteshassar/reactions-to-metricbot/embed" width="100%" height="750" frameborder="no" allowtransparency="true"></iframe><script src="http://storify.com/belteshassar/reactions-to-metricbot.js"></script><noscript>[<a href="http://storify.com/belteshassar/reactions-to-metricbot" target="_blank">View the story "Reactions to @metricbot" on Storify</a>]</noscript></div>
