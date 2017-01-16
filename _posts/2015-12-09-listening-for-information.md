---
layout: post
title:  "Listening for Information"
date:   2015-12-09 16:16:01 -0600
categories: Music
---


Have you ever been in conversation with someone when you miss the last sentence they said. Maybe they weren't clear or you weren't paying attention. You ask them to repeat themselves but just as they're about to speak your brain pops out a sentence and you think, "Ah, that's what it was."

This happens to me all the time. What it demonstrates is that the brain is continuously processing auditory stimulus even seconds after it was received.

We all know that listening is not purely a mechanical process. Though listening is dependent on physical sound waves, the perception of that sound is dependent on the internal state of the mind of the listener. Now that's fairly obvious, but how does one go about demonstrating the role of the internal state of mind? One way is through an auditory illusion.

I've distorted an audio clip of myself speaking. Take a listen and see if you can hear what I'm saying.

<div>
	{% include audio.html name="s1_transformed.wav" %}	
</div>

Now check out the recording of the original sentence below and when you're done listen to the distorted version again.

<div>
	{% include audio.html name="s1.0.m4a" %}	
</div>

The strange thing is now all you can hear is the original sentence. In a way it's impossible to go back to hearing the gibberish.

To understand why this works it's important to know what changed during the transformation. The transformation I put the sample through was just a pitch and phase shift. So although the words don't sound like words, a lot of information is still preserved. For starters intonation, pause and rhythm are all still there.

This is really important because these are aspects of what linguists call prosody - how we say units of speech. Interestingly, if you put a computer generated voice through this transformation it's impossible to hear the sentence. That's because the original recording of the computer never had the "human" aspects of prosody.

The prosody hypothesis was recently strengthened in my mind when I tested a large group of people. The few people in the audience who didn't hear the original sentence in the distorted audio were all people whose second language was english. They spoke english proficiently but all had accents (though some were very subtle). If the only thing preserved in the distorted audio was prosody structures, then it makes sense that they weren't able to understand it.

This experiment has some interesting consequences, which I'll hopefully talk about in another post.

---

This was a final project for [PLAI 600](http://iplai.ca/what-we-do/teaching-and-learning/plai-courses/), a music and listening graduate seminar at McGill University. Also a special thanks to Marc Burns for his help with the audio manipulation programming. This project was inspired by a demo from Scientist Jayatri Das [here](https://www.fi.edu/scientists/jayatri-das-phd)



