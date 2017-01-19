---
layout: post
title:  "Flying Keyboard"
date:   2016-02-23 16:16:01 -0600
categories: Projects
---

Try and figure out how this works before you read on.

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/gvE4XgJ3HWY' frameborder='0' allowfullscreen></iframe></div>

It's not hard to understand how it's done, but more importantly why is it interesting?

Augmented reality is weird because it's familiar but different at the same time. If you were seeing the keyboard and computer display this wouldn't be interesting. If the keyboard were a virtual keyboard, projected onto the table then this would lose its magic as well.

So what exactly do we have?

A physical keyboard and virtual letters (under gravity and collisions), projected onto a physical surface (in close proximity to the keyboard).

It's just the right amount of real and not real.

---
This project was inspired by the [identical demo](https://twitter.com/moment_factory/status/666625677165113344){:target="_blank"} by Moment Factory. I reverse engineered their process and programmed this using Apple's Swift and Sprite Kit. The code is [here](https://github.com/KayhanQ/FlyingKeyboard){:target="_blank"} on github.