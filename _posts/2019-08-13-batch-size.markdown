---
layout: post
title: "The Code Review Batch Size"
date: 2019-08-13 8:00:00 +0000
---

In the [last article](https://blog.codereview.chat/2019/07/15/the-code-review-bottleneck.html) we learned how important it is to reduce the friction in code reviews, by making code reviews your top priority. Quick recap: based on the theory of constraints, when your bottleneck is over capacity, doing work in other places will be counterproductive. If your code review queue is backed up, writing more code will only make matters worse.

The theory of constraints has a solution for increasing throughtput. Decrease your batch size as possible. For us developers the batch size is the number of features that we put into each release or if we are agile and only release one feature per release, the amount of code released for said feature.

If you are reviewing and deploying multiple features in batch because it sounds like this will increase productivity you are doing the exact opposite. By batching features together you prevent small changes from going out while the issues with the bigger changes are being worked out. This is how you end up on a release schedule that takes months is always late and causes havoc when deployed to production in the form of blocker bugs.

# Problem with big pull requests

We developers have this joke that a 5 line pull request will have at least 5 comments and change requests while a 500 line pull request will only have 1: LGTM.

This is due to the fact that to understand those 500 lines the reviewer needs to take a lot of time to write thoughtful comments and often the sheer size of the changes can demotivate them from doing a good job.

# Batching features

If this sounds familiar then the first way to improve your throughtput and regain your sanity is to split features into separate code reviews and then releases.

You can usually notice multiple features in a pull request when the title has the word **and** in it.

Examples:

Fix production issue *and* improve logging

Add new form verification *and* handle edge case when the user is not defined

When reviewing this code a problem with the code that added logging will delay the merge of the code that fixes a production issue. This is going to be counterproductive especially since your users don't care how you log things.

When you write *and* in your PR titles consider opening two pull requests instead. This will also help the reviewed focus on one problem in the pull request making it less likely for mistakes to go through.

This rule is even more important when the code gets deployed. If there is something wrong with the code that improved logging you might have to revert the production issue along with the logging change.

# Batching code

So you took care of your development process and now only deploy one feature at a time, but are still having issues with big pull requests since features that are useful to your customers tend not be just a change to a few lines of code, but instead require days or even weeks of work to be useful. 

Checkin in code after weeks of work tends to be disastrous especially if it's done right before the deadline. The only solution to this is decouple features from our code review and deployment process.

# Decouple Features From Code Changes

Your code review process should not require you to only start reviewing when the feature is done.

# A huge Pull Request

The first way to push a big feature into prod is to open a big pull request with 1000s of lines changed. The problem with this is that the code will be hard to review and hard to deploy and you might have bugs popping up in unexpected places.

# Feature Branches

Feature branches allow you to decouple code reviews from the feature itself. You create a new branch and use it for all development for the feature. You can enforce that all changes that go into the feature branch need to be reviewed before the merge.

This helps you improve your code review process, but it has a few unwanted side effects. Feature branches tend to create a big chunk of code with a lot of changes that will probably be extremely difficult and risky to deploy.

Maintaining a feature branch also tends to be painful as changes from the development branch constantly need to be merged in. The more changes the feature branch contains the more frequent merge conflicts happen and the more likely it is that they will be resolved incorrectly, creating bugs in your system.

Lastly, since merges aren't getting deployed, the reviews tend to be more leniant - thinking that issues will be addressed further down the development process of the feature. The problem is that this often doesn't happen and bad poorly reviewed code makes it into produciton.

# Trunk Based Development

The only way to address these issues is to avoid having long running feature branches in the first place. Instead, all the changes should go directly into trunk. This sounds scary since it makes you put unfinished features into production.

This will force you to change the way you write code since it will require you to decouple the code changes from the feature. You will have to use code gating, feature flags and other concept to make sure that the unfinished features won't cause issues when deployed.

But you will make your review process better - the changes going into trunk will be small and easy to review.
