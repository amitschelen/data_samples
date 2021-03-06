# The Monty Hall Problem

The Monty Hall Problem is a classic probability puzzle that people often find unintuitive. The basic premise is taken from the game show “Let’s Make a Deal” and the problem get’s its name from the show’s host, Monty Hall. At the end of the show, the grand prize (car) was hidden behind one of three doors. The other two doors concealed much less desirable prizes called “zonks.” For the purposes of my analysis, I have taken the zonks to be goats. 

![not a goat](https://github.com/amitschelen/Monty-Hall/blob/main/2009lmadzonkgoat.jpg "not a goat")

*(nb: not a goat)*

[Photo from Wikipedia](https://en.wikipedia.org/wiki/Let%27s_Make_a_Deal#/media/File:2009lmadzonkgoat.jpg)

## Probabilities
So…three doors…one prize…two zonks.  Contestants first pick one of the three doors. This has a 1/3 probability of concealing the prize. But the twist is that the host then opens one of the other doors. The other door is always a zonk and never the door that was already picked. The contestant is then given the opportunity to stick with their original selection or switch to the remaining unopened door. This is where things get interesting. Many people incorrectly judge the probability associated with switching doors. Some people reason that that the car is behind one of the doors, so there’s a 50/50 chance either way so it doesn’t matter. Some people think that it’s still a 1/3 probability that the car is behind either door. But neither of these are correct.

The correct answer is that the contestant should always switch because the probability of getting the car by switching is actually 2/3. So a contestant would double their chance of winning by switching. Why? [Here’s a link](https://www.youtube.com/watch?v=mhlc7peGlGg) to a video that explains it better than I can.   But the gist is that if a zonk was originally selected (which would happen 2/3 of the time), then the door the host opened was definitely a zonk. So if the contestant switches in that situation, they will definitely switch to the car. That means if you pick a zonk first, you’ll always get the car by switching. And that happens 2/3 of the time.

I was curious how the Monty Hall problem worked with more than three doors. It seemed easiest to [run through it with python and see what happened.](https://github.com/amitschelen/Monty-Hall/blob/main/monty_hall_stats.py "the model") While I was at it, I made [a functional version of the game.](https://github.com/amitschelen/Monty-Hall/blob/main/monty_hall_game.py) In the game, players have the option to switch or not. But in the model, the door is always switched since that is the probability I wanted to explore. Is the probability of winning by switching always twice as high? I didn't think so. Or maybe it isn't affect with more than three doors since the wrinkle of being guaranteed to swich to the car when you initially pick a zonk is unique to three doors? That didn't seem right either. It seems like opening a door should always do *something*.

## Results
For **n** doors, the probability of getting the prize without switching is easy. That's just **1/n**. The results of the model show that the formula for getting the prize by switching is always **(n-1)/n(n-2)**. I interpret this as the product of two events; First you pick a door with a zonk (if you pick the car first then switch, you definitely lose) which has **(n-1)/n** probability (**n-1** zonks out of **n** doors). Then you switch to the car and that has **1/(n-2)** probability (**1** car out of the **n-2** remaining available doors). This gives the following probabilities of winning the car for 3, 4, and 5 doors. Explore the model to find probabilities for more doors.

3 doors - Don’t switch:   1/3   Switch:   2/3

4 doors – Don’t switch:   1/4   Switch:   3/8

5 doors – Don’t switch:   1/5   Switch:   4/15

As you can see, the probabilities of winning by switching and not switching grow closer together as more doors are introduced. This is reasonable since the effect of opening a door (removing the chance of picking one of the zonks) is diminished with more and more doors. Eventually with 100 doors, the probabilities of winning by switching and not switching are approximately the same. Check out [the model](https://github.com/amitschelen/Monty-Hall/blob/main/monty_hall_stats.py "the model") or [the game](https://github.com/amitschelen/Monty-Hall/blob/main/monty_hall_game.py) to explore these situations further.
