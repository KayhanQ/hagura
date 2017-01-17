---
layout: post
title:  "A Family of Fibonacci"
date:   2016-02-25 16:16:01 -0600
categories: Math
---

There are a lot of integer sequences. Some of them I'm sure you're familiar with like the Fibonacci sequence.

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181...

Others are more exotic like the Hofstader Q-Sequence.

0, 1, 1, 2, 3, 3, 4, 5, 5, 6, 6, 6, 8, 8, 8, 10, 9, 10, 11, 11, 12, 12, 12, 12, 16, 14, 14...

What's interesting is that these two sequences are in the same family. That's just another way of saying that they're generated in a similar way. 

Here's the recurrence relation for the Fibonacci sequence.

{% highlight tex %}
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2)
{% endhighlight %}

And here is the Hofstader Q-Sequence.

{% highlight tex %}
Q(0) = 0
Q(1) = 1
Q(n) = Q(n-Q(n-1)) + Q(n-Q(n-2))
{% endhighlight %}

While it looks more complicated if you work through it, it isn't very different. The terms of the Fibonacci sequence are determined by summing the two preceding terms. The Q-Sequence on the other hand takes the two preceding terms and uses them to find two more terms.

So what would the next sequence in this family of sequences be? Let's follow the pattern and make a new sequence. We'll call it R.

{% highlight tex %}
R(0) = 0
R(1) = 1
R(n) = R(n-R(n-R(n-1))) + R(n-R(n-R(n-2)))
{% endhighlight %}

That's seems to look right. However, R(3) doesn't actually exist. That's because when we try to calculate R(3) we end up looking up a number at a negative index. But there is no R(-6) for example, so it breaks. It's worth mentioning that no one is sure if the Q sequence goes on forever. It may just be that at some point it also terminates like this.

It's not great that the sequence looks up a negative index but perhaps we can fix this. Let's say we're computing up R(3), we could mod all indices by 3 to make sure they are in our bounds. Now R is defined for any n. The recurrence relation would look like this.

{% highlight tex %}
R(n) = R((n-R((n-R((n-1)%n))%n))%n) + R((n-R((n-R((n-2)%n))%n))%n)

R(n) = R(-R(-R(-1%n)%n)%n) + R(-R(-R(-2%n)%n)%n)
{% endhighlight %}

Note that we cleaned the formula up a bit since (n-a)%n is just -a%n. With this we get the generated sequence:

0, 1, 1, 2, 3, 5, 8, 16, 0, 0, 0, 0...

It's not a very exciting sequence but it does exist. We can now redefine F and Q with these modular bounds. Note that this new squence F is exactly the same as the original Fibonacci Sequence.

{% highlight tex %}
F(n) = F(-1%n) + F(-2%n)

Q(n) = Q(-Q(-1%n)%n) +Q(-Q(-2%n)%n)
{% endhighlight %}

Now we have a consistent family of sequences. Let's call them S sequences where:

{% highlight tex %}
S0 = S0(-1%n) + S0(-2%n)

S1(n) = S1(-S1(-1%n)%n) + S1(-S1(-2%n)%n)

S2(n) = S2(-S2(-S2(-1%n)%n)%n) + S2(-S2(-S2(-2%n)%n)%n)

...
{% endhighlight %}

Here are the first few terms of the first 10 S sequences.

{% highlight tex %}

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610, 987, 1597, 2584, 4181...

0, 1, 1, 2, 3, 3, 4, 5, 5, 6, 6, 6, 8, 8, 8, 10, 9, 10, 11, 11, 12, 12, 12, 12, 16, 14, 14...

0, 1, 1, 2, 3, 5, 8, 16, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...

0, 1, 1, 2, 3, 3, 4, 6, 4, 5, 7, 9, 9, 8, 9, 11, 9, 10, 12, 16, 16, 10, 16, 17, 13, 20, 16, 21...

0, 1, 1, 2, 3, 5, 8, 16, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...

0, 1, 1, 2, 3, 3, 4, 6, 4, 5, 7, 10, 5, 6, 12, 7, 20, 19, 39, 39, 2, 41, 4, 4, 4, 82, 8, 90, 6...

0, 1, 1, 2, 3, 5, 8, 16, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...

0, 1, 1, 2, 3, 3, 4, 6, 4, 5, 7, 7, 8, 8, 8, 14, 5, 10, 14, 15, 12, 13, 12, 28, 20, 21, 22, 21...

0, 1, 1, 2, 3, 5, 8, 16, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0...

0, 1, 1, 2, 3, 3, 4, 6, 4, 5, 7, 9, 8, 8, 12, 18, 12, 15, 8, 15, 11, 9, 19, 15, 17, 22, 24, 9, 26...

{% endhighlight %}

If you generate more of the sequences you'll notice that the even numbered sequences also seem to turn into 0's as they grow. There's some interesting things we can do once we have generalized the Fibonacci sequence, which I will talk about in a follow up post.