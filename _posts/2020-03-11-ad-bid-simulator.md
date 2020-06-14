---
layout: post
title:  "Ad Bid Simulator"
date:   2020-03-11
excerpt: "Ad is the major monetizing product for many companies. Here I'll introduce how I build the simulator to evaluate and develop the ad system in indeed."
<!-- project: true -->
tag:
- ad
- bidder algorithm
- simulator
feature: assets/img/blog/ad3.png
comments: true
---

## Intro

Ad is the major monetizing product for many companies. Here I'll introduce how I build the simulator to evaluate and develop the ad system in indeed.

Here's the slide:

<center>
<iframe src="//www.slideshare.net/slideshow/embed_code/key/jV3bl7ZSiGpZp6" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/marsanmars/ad-science-bid-simulator-public-ver-229698886" title="Ad science bid simulator (public ver)" target="_blank">Ad science bid simulator (public ver)</a> </strong> from <strong><a href="https://www.slideshare.net/marsanmars" target="_blank">Marsan Ma</a></strong> </div>
</center>

## The difference of DSP and "when you own the whole system"

![ad1][ad1]

When you're just a DSP company, you could treat the external world like they're static, and do your A/B test normally. Since your effort to the whole bidding world is tiny, your algorithm change cannot really change the whole bidding eco-sysyem hugely.

But when you own the system, things are very different: whatever your algorithm change, it will ramp-up to 100%, and it will change the world --- which means what you see in 1% A/B test will be different as you ramp-up.

While we separate ads into control and treatment groups and bid with old and new bidding algorithm accordingly, they're still bid together, so they *will have network effect*. Besides, ad product always has terrible seasonality concerns, making online test volatile.


![ad2][ad2]

![ad3][ad3]

![ad4][ad4]

![ad5][ad5]


[ad1]: /assets/img/blog/ad1.png
[ad2]: /assets/img/blog/ad2.png
[ad3]: /assets/img/blog/ad3.png
[ad4]: /assets/img/blog/ad4.png
[ad5]: /assets/img/blog/ad5.png
