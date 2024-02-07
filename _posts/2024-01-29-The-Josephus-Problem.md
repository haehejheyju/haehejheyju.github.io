---
layout: page
title: The Josephus Problem
permalink: /maths/
date: 29th Jan 2024
---

**HISTORY**
{:.lead}

The problem probably dates back to the "decimatio", the collective punishment practised by the Roman army where every tenth man in a detachment was chosen by drawing lots and punished. In literature, it is linked to an event that occurred in the life of the Jewish historian Flavius Josephus in 67 A.D. – hence the name "the Josephus problem": when the city of Yodfat was besieged by the Roman General Vespasian, the Jewish soldiers decided to commit collective suicide. Nonetheless, Josephus was afraid to disagree so he suggested to arrange themselves in such a way that he and his best friend remained at the end after drawing lots.

A [reference link 1](https://library.ethz.ch/en/locations-and-media/platforms/virtual-exhibitions/Its-all-math-and-games/the-josephus-problem.html) to the ETH Bibliothek.<br>

![image](/assets/img/TheJosephusProblem/tjp1.jpg){: width="250" }

**RULE**
{:.lead}

The Jewish soldiers would arrange themselves in a circle, and the 1st soldier would kill the person to the left of him - hence in clockwise direction. The next remaining living soldier would kill person to the left of him, and it repeats until only one person is left. As Josephus wanted to survive, he had to figure out WHERE  he should sit within the circle.

Refer to the examples below:

![image](/assets/img/TheJosephusProblem/tjp2.jpg)
![image](/assets/img/TheJosephusProblem/tjp3.jpg)

**PATTERNS VIA TRIAL & ERROR**
{:.lead}

|--------------+-------------------------|
| n {soldiers} | W(n) {winning position} |
|--------------|:------------------------|
|       1      |            1            |
|       2      |            1            |
|       3      |            3            |
|       4      |            1            |
|       5      |            3            |
|       6      |            5            |
|       7      |            7            |
|       8      |            1            |
|       9      |            3            |
|      10      |            5            |
|      11      |            7            |
|      12      |            9            |
|      13      |           11            |
|      14      |           13            |

*  The winning position is always ODD.
*  All the EVENs get killed in the first loop.
*  Value of W(n) increases by 2 each time, but it resets at some point.

When do we reset? Where do we get the 1?
As we refer to the table, we can identify that the n that gives W(n)=1 are always power of 2. Hence, we can now guess that if n=15, then W(n)=1 .

**CONJECTURE**
{:.lead}

Now, we have to state a conjecture and then prove a theorem based on what we just identified here.

Conjecture: If n = 2^x then W(n) = 1

e.g. n=2^4=16.

1. Remove all the evens (according to the rule):
![image](/assets/img/TheJosephusProblem/tjp4.jpg)

2. Put a dot on 1 so we can remember that it is 1’s turn again. When I relabel at this point, n=2^3=8 - the number of remaining ones are powers of two again:
![image](/assets/img/TheJosephusProblem/tjp5.jpg)

3. It’s still 1’s turn after the second round. So I go through again:
![image](/assets/img/TheJosephusProblem/tjp6.jpg)

4. 1 wins: 
![image](/assets/img/TheJosephusProblem/tjp7.jpg)

**WHAT ABOUT n≠2^x?**
{:.lead}

We have figured out what happens for W(n) of n=4 and n=8 ,  but not for W(n) of n between n=4 and n=8.

|--------------+-------------------------|
| n {soldiers} | W(n) {winning position} |
|--------------|:------------------------|
|       4      |            1            |
|       5      |            3            |
|       6      |            5            |
|       7      |            7            |
|       8      |            1            |

Let: n = 2^x + a

Take the biggest 2^x you can subtract from the *n* and of course, *a* should be smaller than the 2^x.
Also, when you express the number in binary notation, the 1s show 2^x, so choose the biggest one.

e.g.

13 = 2^3 + 2^2 + 2^0 = 1101
The biggest one is 2^3. 
Hence n = 8 + 5

1. According to a = 5, go 5 steps:
![image](/assets/img/TheJosephusProblem/tjp8.jpg)

2. Now I have dropped a people, and it is number 11’s turn:
![image](/assets/img/TheJosephusProblem/tjp9.jpg)

3. 8 people, AKA 2^3 people are left. We know who wins in a power of two, it’s whoever starts. Therefore, if I go from number 11, number 11 wins. 
![image](/assets/img/TheJosephusProblem/tjp10.jpg)

Which is, if a number is written as 2^x + a , whichever turn it is after *a* steps wins. 
After trying few times with other numbers, we can identify that W(n) = 2a + 1 .

If n = 2^x + a where 2^x > a
then W(n) = 2a + 1

|--------------+---------+----------------------------------|
| n {soldiers} | 2^x + a | W(n) = 2a + 1 {winning position} |
|--------------|---------|----------------------------------|
|       1      |   1+0   |            2(0)+1=1              |
|       2      |   2+0   |            2(0)+1=1              |
|       3      |   2+1   |            2(1)+1=3              |
|       4      |   4+0   |            2(0)+1=1              |
|       5      |   4+1   |            2(1)+1=3              |
|       6      |   4+2   |            2(2)+1=5              |
|       7      |   4+3   |            2(3)+1=7              |
|       8      |   8+0   |            2(0)+1=1              |
|       9      |   8+1   |            2(1)+1=3              |
|      10      |   8+2   |            2(2)+1=5              |
|      11      |   8+3   |            2(3)+1=7              |
|      12      |   8+4   |            2(4)+1=9              |

**FUN FACT (Perhaps a trick?)**
{:.lead}

A number (denary AKA decimal), can be re-expressed in binary notation.

e.g.

n = 41 = 2^5 + 2^3 + 2^0 
equals to
101001

It is noticeably faster to find W(n) in binary notation as all you need to do is to take the most significant bit (MSB), and put it at the end, letting it to be the least significant bit (LSB).
![image](/assets/img/TheJosephusProblem/tjp11.jpg)

A [reference link 2](https://youtu.be/uCsD3ZGzMgE?si=0loMzhJdAZgvHRdZ) to Numberphile (YT).<br>

TO CONCLUDE,
{:.lead}

The Josephus problem is a well known puzzle in Mathematics and Computer science; some even claim that it is an ancient Maths problem beloved by many Computer scientists. Although the proofs above are done by mathematical means, the concept of this problem is also applied in Computer science to computer algorithms, data structures, and image encryption. The proof I have shown above is the simplest approach to solve the Josephus problem, I suppose. Nonetheless, I believe this was more than enough to boost my enthusiasm towards solving problems or theorems that both Mathematics and Computer science intersect. ~~I could have done a deeper research on the Josephus problem - the one with more ‘advanced’ maths equations, but I just could not wait to upload my first post on my GitHub hosted website!~~ I should, perhaps, re-approach the Josephus problem with codes or that ‘advanced’ maths equations in the not-too-distant future to obtain a wider perspective of understanding certain problems.