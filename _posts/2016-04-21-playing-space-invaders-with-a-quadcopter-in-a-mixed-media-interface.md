---
layout: post
title:  "Playing Space Invaders with a Quadcopter in a Mixed Media Interface"
date:   2016-04-21 16:16:01 -0600
categories: Projects
---

<p>
	{%include image.html name="cover.png" caption=""%}
</p>

Augmented reality is a form of mixed media where virtual objects are projected into the physical world. This project focusses on potential roles robots could play in creating novel mixed media interfaces. Our primary reference paper is [Mechanical Constraints As Computational Constraints in Tabletop Tangible Interfaces](http://dl.acm.org/citation.cfm?id=1240746){:target="_blank"} by James Patten and Hiroshi Ishii. We believe this field of augmented reality has been underdeveloped and that the technologies exist to create simple, useful and novel interfaces.

Specifically we discuss the implementation and challenges of our variation on the classic arcade game, Space Invaders. In our variation the game is projected onto a wall, but instead of having a projected spaceship the player pilots a physical quadcopter. The quadcopter is tracked using a camera so that its position can be accurately represented in the game. The quadcopter is piloted up and down in order to dodge lasers from the invades and to return fire.

For this project we decided to use a tracking and simulation approach. We first tracked the position of the quadcopter and then simulated it in our game. To convert the coordinates of the camera space to the game space we used fiducial markers for calibration. We tested multiple approaches towards calibration and tracking. For our tracking approach we settled on using four fiducial markers and a perspective transform to map the coordinates of the quadcopter. This approach gave us the most accurate results. For tracking the quadcopter we applied multiple thresholds to our image and then applied the Canny Algorithm.

<div>	
	{%include image.html name="fiducial_1.png" caption=""%}
</div>

A major limitation of our current system relates to inaccuracies in tracking at certain positions. Because we make the assumption that our quadcopter is a flat object on the plane of our wall when our camera is placed either very low, looking up, or very high, looking down we receive an inaccurate localization. For example when we detect our quadcopter from below we imagine it being higher than it actually is as the line of sight is projected up to the wall.

Again, we do not want the z coordinate of the projection of the camera onto the wall, but we want the z coordinate of the quadcopter from the point of view of a player looking straight onto the wall. We could attain this value by taking the y coordinates into account and using the projection model. The distance from the wall to the projector could be measured as well as the expected distance from the quadcopter to the projector (this could be also computed on the fly by using the quadcopter's measured width). These coordinates would be used along with the perspective transform to adjust the tracking coordinates for a view straight onto the wall which is what we require for our pseudo 2D game.

The tracking system we have developed could easily be applied to any other simple game. An example of a possible follow up to this project would be implementing Breakout using a ground robot as the paddle. This system could also be extended for other mixed media interfaces, for example, to display origami instructions on a piece of paper as it is being folded on a flat surface.

<div>
	<iframe width="560" height="315" src="https://www.youtube.com/embed/w3Eru1b7DLI" frameborder="0" allowfullscreen></iframe>
</div>


---

This was a final project for COMP 417 (Intro to Robotics) taught by Prof. Gergory Dudek and Prof. David Merger at McGill University in Winter 2016. The paper can be found [here]({{ site.baseurl }}/assets/posts/{{ page.date | date: "%Y-%m-%d" }}-{{ page.title | slugify }}/quadcopter-space-invaders-paper.pdf){:target="_blank"}. Code for the project can be found [here](https://github.com/KayhanQ/Farquad){:target="_blank"} on Github.