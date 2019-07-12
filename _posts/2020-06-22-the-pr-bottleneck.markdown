---
layout: post
title: "The Code Review Bottleneck"
date: 2019-07-10 12:39:52 +0000
---

Code reviews are [insanely useful](https://blog.codereview.chat/2019/06/27/code-reviews-and-your-company-goal.html), but they have the nasty habit of making your cool new feature stuck in the queue waiting for reviewers. Let's take a look at how to make sure code reviews are done as efficiently as possible and how to make sure they don't impede your feature velocity.

# The Bottleneck

Code reviews are by their nature a bottleneck. They slow down the flow of features on their way to production. In this sense they work against the main goal of the engineering team in your company which is to ship quality features to customers as soon as possible. But because code reviews help your team ship fewer bugs and higher quality features it's worth the downside.

If your pull requests are pilling up and staying open for weeks it might be a sign that your process could use some improvement.

Remember, the faster you can ship new features the better your company can adjust to new market trends and resolve user issues. Teams that can deliver in weeks outperform teams that deliver in months or even years.

# The Wait Time

The biggest issue with code reviews is the wait time.

When the author of the code opens a pull request and marks it ready for review, they need to **wait** until another person comes along and reviews it. This could be 1 hour after the pull request has been opened (if you are lucky) or it might take a few days or even weeks (if you are not).

After the first review is posted there is almost always a bit of wait time again, before the author sees the review, and then even more if the author needs to adjust the code based on the feedback.

This process can go on for multiple cycles and every handoff adds another bit of wait time. This is how a simple feature that was ready 2 weeks ago still has a pull request open and hasn't shipped yet.

The wait time is especially painful for us programmers because after each wait time, the context is lost and needs to be rebuilt again from scratch. The longer the wait time the more difficult it is to remember how all the line changes fit together into the shippable feature.

# The Solution

There is only one way to resolve the wait time issue. It is to try to minimize it as much as possible. The best way to accomplish this is to make code reviews **the top priority** for your team.

When a pull request is ready for review, the reviewers should drop everything and focus on getting it reviewed and merged ASAP, the wait time between handoffs should be measured in minutes and not hours or bob forbid days.

When a pull request is reviewed and needs updates, the author should drop everything else that they are working on and respond to the comments. Again limiting the wait time to minutes not hours if possible. If the review requires a substantial amount of code changes you should discuss it with reviewers and make sure these changes will bring business value to customers.

This rule of drop everything because of code reviews is counter intuitive for us developers because we like to be in the flow and don't want to break out of it for whatever reason. This is how we feel productive. Code reviews don't make us feel productive because we will not be credited when the feature ships. Usually it's the author that will take all the credit.

If you follow the rule of code reviews being the top priority your personal productivity will fall and you will not feel good about it.

# But the productivity of your team will soar

The harsh reality is that your personal productivity is nowhere as important as the productivity of your whole team. Your team is most productive when it's shipping features to your users. When a feature is ready for code review the developer is saying it's ready to be deployed to production. Your team's most important goal at this point is to verify if this is true and do everything possible to get it out the door.

Anything other than doing the code review is counter productive for your team. If you spend the rest of the day working on your feature instead of reviewing a pull request from your coworker, you're blocking a feature from being deployed and even worse, you are creating a new bottleneck in the form of your own pull request that you will open when your feature is ready. This is how pull requests pile up and nothing gets shipped.

It's absolutely crucial to make the code reviews the top priority. When a code review comes in stop all other non productive activity - which is pretty much anything except maybe firefighting a production issue affecting your customers.

You will be my hero if you say that the current meeting needs to end earlier because you need to go review a pull request that was just marked as ready for review.

In the next blog post we'll take a look at some techniques you can use to make it possible to review and merge as quickly as possible. Spoiler: it's all about reducing the batch size!
