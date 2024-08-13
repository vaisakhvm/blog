---
layout: post
title: "Recognizing Cognitive Bias in Problem Solving: A Vital Lesson"
date: 2024-08-13
---

I recently hit a snag with my [Jekyll](https://jekyllrb.com/) blog where the CSS from my theme `gem` wasn't updating after deployment to GitHub Pages. My knee-jerk reaction was to blame [Bundler](https://bundler.io/) cache, as it had caused similar issues recently on my local machine. A quick `bundle update gem` had fixed the problem locally, so I naturally assumed the same issue might be affecting my GitHub Pages deployment.

However, after checking the site on a different computer, I discovered the CSS updates were actually applied correctly. This made me realize that the issue was not with Bundler or GitHub's deployment pipeline but likely related to browser caching.

This incident was a clear example of [Confirmation bias](https://en.wikipedia.org/wiki/Confirmation_bias), where we focus on information that confirms what we already believe. When I saw the CSS wasn't updating, I quickly blamed the Bundler cache because it was a recent issue I had solved. I didn't investigate further and just assumed the new problem was the same, reinforcing my initial thought.

### What I Learned
**Question your assumptions**: Before jumping to conclusions, take a step back and critically evaluate your assumptions. Ask yourself if there could be other explanations for the issue at hand. <br/>
**Gather more evidence**: Instead of immediately acting on your first instinct, gather additional data or test your hypothesis in different ways. In my case, checking the site on another machine provided new information that contradicted my initial assumption. <br/>
**Stay open to new information**: Be willing to change your mind when new evidence emerges. It is easy to get attached to a particular solution, but flexibility is key to effective problem solving.


The experience of misattributing a CSS update issue to Bundler cache serves as a reminder of how cognitive biases can influence our decision making. By staying aware of these biases and actively working to counteract them, we can improve our problem solving abilities and make more accurate, informed decisions in our technical work and beyond.

Recognizing and addressing cognitive bias is not just about solving technical issues, it is a valuable skill that enhances critical thinking and leads to better outcomes in all areas of life.