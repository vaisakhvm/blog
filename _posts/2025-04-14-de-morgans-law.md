---
layout: post
title: "De Morgan's Law in SQL"
date: 2025-04-14
categories: [sql]
tags: [sql, logic, demorgan]
---

Logic can quickly become convoluted when you start nesting `NOT`, `AND`, and `OR` in SQL.
[De Morgan's Law](https://en.wikipedia.org/wiki/De_Morgan%27s_laws) provides a way to simplify.
#### The Law

$$\neg (A \land B) = (\neg A) \lor (\neg B)$$

$$\neg (A \lor B) = (\neg A) \land (\neg B)$$

This gives us a way to rewrite negated conditions into something more readable in SQL.

Imagine you need to find users who are **not from India or the USA**.

A common approach:
{% highlight sql %}

SELECT * FROM users
WHERE NOT (country = 'India' OR country = 'USA');
{% endhighlight %}

Using De Morgan's Law, you can simplify:

{% highlight sql %}
SELECT * FROM users
WHERE country <> 'India' AND country <> 'USA';

{% endhighlight %}

It is logically equivalent and simpler.

