---
layout: post
current: post
cover: assets/images/advanced.jpg
navigation: True
title: Machine Learning Summer Schools
date: 2018-10-16
tags: [summer-school]
class: post-template
subclass: 'post tag-summer-school'
author: swapneel
---

*This post is the first in a series of posts highlighting my attempt(s) to prepare myself to undertake research and for graduate school. It will include a year in review, learnings from working at CERN, and some technical posts about the kind of work I do.*


### Background

I’m a recent graduate of Computer Engineering working at the European Organisation for Nuclear Research (CERN). I got into a "US top-15" school for pursuing a Masters in Computer Science starting 2018 but chose to work as a Technical Student for a year instead. My goal in spending this year at CERN is to to gain more perspective and better understand my interests before diving straight into graduate school. As I worked on [projects](https://github.com/DL4Jets/DeepJetCore) at the CMS Experiment, I really developed a strong liking for problems we face in high-energy physics. This series of posts will serve as a reflection of the people I have met and experiences I have shared over the past summer.


### Applying to Summer Schools

The year started on a mixed note;  I was excited about working at CERN, but also wondering what directions to take in order to prepare for graduate studies. My aim is to learn by doing and make the most of opportunities that come along. So I decided to figure out how to improve my knowledge of machine learning that was essentially self-taught—taking online courses and working on a project aiding the deployment Tensorflow models in production on the CMS Software Environment. I spent two weeks researching and applying to machine learning summer schools with my supervisor (and former supervisor) supporting me with reference letters wherever necessary.

The schools had some really cool speakers lined up which I thought would make for a great introduction to subjects like gaussian processes, natural language processing, causal inference, probabilistic methods, bayesian non-parametrics, and optimisation. The application process for the schools was fairly straightforward (often doing away with the reference letter) and encouraged students to present posters of their ongoing/completed projects. I ended up visiting two schools - Machine Learning in High-energy Physics Summer School (Oxford, UK) and Machine Learning Summer School (Madrid, Spain), apart from the Deep Learning Indaba (Stellenbosch, SA). My poster on our work (DeepJet) was presented at MLSS and the Indaba. 

*Note: I learnt later how presenting posters forms a critical part of the experience; it fosters discussions on a plethora of interconnected domains promoting quick and reliable knowledge transfer. As Jeff Dean said in a talk at the Deep Learning Indaba, “If I had a choice between reading one research paper in great depth or just skimming through ten papers, I would choose the latter because that gives me a broader idea of the problem space that I can then build upon.” Poster presentations accomplish pretty much the same goal and in addition foster collaboration and interest in relevant work by others you may not otherwise hear of.*

*Note: I also learnt later how lucky I was to have qualified for these events that are otherwise primarily targeted at an audience of Ph.D. students (except for the Deep Learning Indaba). This gave me an invaluable set of opportunities to connect with researchers and graduate students who were perfectly equipped to offer **relevant** advice to me (a lot of people can offer advice, but very little is often relevant).*

## Takeaways

Here’s a brief outline of each of these events along with what I learnt from each of them. In this post, I've focused on the [Fourth Machine Learning in High-energy Physics Summer School](https://indico.cern.ch/event/687473).

### MLHEP 2018:  
The Machine Learning in High-energy Physics Summer School was organised by researchers from Yandex, Skoltech, and HSE at Oxford University in the UK. It is an event targeted at Ph.D. students and Professors in Physics seeking a foothold in machine learning to find applications to their respective problem statements. However, given that I was working on a project along similar lines, it served as a pretty good primer for me.
	
##### School Highlights
* The school began with two tracks—one slightly more advanced introduction and another for beginners to programming and data science. 
* The lectures adhered to a (really useful) hands-on format where each talk was followed by a practical coding session teaching the practical uses of each model.
* The [MLHEP Starter code](https://github.com/yandexdataschool/mlhep2018) was really well documented and overall quite thorough in its treatment of the subject. It should serve as a useful reference even for those who have not attended the event.
* There was a set of invited lectures (one per day) that was truly the highlight of each day. It made me wonder how they shortlisted speakers but whatever the process was, it clearly worked. From an introduction to Quantum Physics and Deep Learning to NVidia's use of AI, to Advertisements on Oracle Data Cloud, and a detailed architectural breakdown of Google's newly introduced Tensor Processing Unit - these lectures did not disappoint! The slides for each of these lectures has been kindly [made available](https://github.com/yandexdataschool/mlhep2018) by the organisers.

**The Codalab Challenge**
* Amidst a packed (read 7:30 am - 7 pm) schedule that prevented me from visiting this popular vegan joint (sadly, it shut by 5 pm daily) we had yet another activity - a multi-phase [Codalab Challenge](https://competitions.codalab.org/competitions/19818) on the Semantic Segmentation of LArTPC ([Liquid Argon Time Projection Chamber](https://en.wikipedia.org/wiki/Time_projection_chamber)) tracks! Phase 1 was now open to us and the rest would follow soon after.
* If you don't understand much about the title, don't be disappointed. I didn't know much about it either. But I did know that we had free GPU Credit and some [starter code](https://github.com/yandexdataschool/mlhep2018-starterkit), and when someone is so kind as to give you a free GPU and some machine learning models, it is only natural for your overfitting instincts to kick into overdrive. So overfitting aside, that's exactly what I did. 
* My first four attempts gave me exactly zero accuracy. I had no idea what I was doing wrong. After 14 hours of training (I woke up intermittently through the night to check up on the model) I realized I was not preprocessing the data correctly. Long story short, after a series of modifications to my code, I arrived upon a seriously crappy model and placed almost last on the leaderboard.

*That was probably my breaking point.*

* Now there were two undergrads at the school who didn't really participate in the challenge (to my knowledge, and based on the leaderboard). The rest of the thirty-ish people were Physics Ph.D. Students. They understood exactly what a [LArTPC](https://en.wikipedia.org/wiki/Time_projection_chamber) was, in addition to having the same starter code and a reasonably good understanding of machine learning. Then there was me - the third undergrad with almost entirely self-taught knowledge of machine learning (I'll write another post sometime about my opinion on the Indian Education System) and barely any understanding of the properties of the track data. Did I really expect myself to miraculously arrive at the optimal hyperparameters for this problem given that I was already drained after 12 hours of attending the school daily?

*Then, I binged on a box of Pringles and reevaluated matters*

* I was an undergrad among 2nd and 3rd year Ph.D. students (also some Professors) and I still managed to not only get in but also successfully understand most of the topics taught in the school.
* The very fact that I had a submission placed me in the top-30% of the school (many people decided against participating due to various issues including the time constraints and a limited understanding of the starter code).
* I did finally start understanding what LArTPC was about, after watching some introductory lectures. It wasn't that complicated. And the history of the TPC was pretty cool (I like reading about the story behind things).
* I used the more complicated model - the Message-passing Neural Network instead of the Convolutional Neural Network simply because I wanted to 'try something new.' I managed my model fairly well by tweaking the learning rate, playing around with dropout to prevent overfitting, switching around optimizers, and adjusting the number of training epochs. The accuracy (to my recollection) was 80-something percent.
* Given that it was my first Kaggle-like challenge, this was a pretty great outcome. Giving up now would be a very silly idea. Either way, there was only a day more left. Instead, why not try to push harder for a day without any expectation and see what I get.

*So I did.*

* For the next three nights, I didn't waste a lot of time on dinner, grabbing what I could from the nearest restaurant. I focused on reading up about the physics end of things and understood what exactly the challenge expected us to do. Then, I dug up some esoteric stuff on graph nets that led me to the conclusion that this was not going to be easy to pick up in a few hours. 
* Earlier I had assumed the code would be easy to tweak since I was looking at it from an outsider's perspective. On diving deeper, I realized that it was "messier" (arguably "over-modularized") than I had thought. Custom functions were called that were defined in separate files and directories and overall it took me a bit of time to try and get it working. To be fair, this was really nice code, but in the time we had it was difficult to digest everything. So I figured out how to use the base architecture, hacked together a working model, and set it training while I read up on how message passing works.
* The next few days were basically low on sleep and high on Tensorboard and excitement. I find that I get really excited about the little things especially when I like what I'm doing. Although I didn't expect to achieve much, what I was doing seemed really interesting so I spent time understanding (or rather hypothesizing) why some models gave me better accuracy and losses but didn't really produce an output as good as others on the test set (overfitting, maybe?). A very naive way of looking at it is that there's tradeoffs between the learning rate you use and the number of training epochs that you need to monitor as the losses go down and accuracy increases. The plot has slight bumps (in the wrong direciton) after a point that seem to tell you that you might be overfitting. 
* I realized it wouldn't be feasible to use all of the training data (I/O was waaaaay too slow) nor would it be easy to create batches currently given the time constraints and custom code (I just had a day left at that point and we still had lectures). These tradeoffs resulted in a lot of updates to my approach and the code, ultimately arriving at a set of models that seemed to do okay, placing somewhere near the upper half of the leaderboard. 
* As the deadline loomed and I submitted my last model, I landed up 4th on the Phase 1 Leaderboard for the challenge with an accuracy of 90-something percent. This wasn't the miracle win I expected (blame Hollywood for setting my expectations high) but it was undoubtedly a decent result for a first-timer given the aforementioned constraints.
* The next morning, the CodaLab Challenge winners were asked to present their models. [Alex](https://github.com/yandexdataschool/mlhep2018/blob/master/day6-Sun/AlexHeld-20180812_MLHEP2018.pdf), who stood first on the leaderboard, came up to explain his entry.
* As I listened to Alex talk about how he visualized the data (used the CNN for visualizing the features? not clear on this) and tweaked the learning rate and a lot of jargon (but in the nice sense), I was very impressed with the work. Having nothing else to focus on as they announced the next winner, I started planning my journey back to Heathrow from Oxford - I didn't want to miss my flight.
* A friend sitting next to me elbows me as he points to the leaderboard. "Isn't that you?" 
"What?"
"`smehta`, that's your username right?"
"Oh, right. Well, shit."
* Mother of God, I stood second. How? Well, you see the challenge had multiple phases, and they simply used the test data from the second phase (only slightly advanced from Phase 1) to evaluate the models. This resulted in some models not performing as well - surprisingly enough, mine did. They had told us this before, and I remember I had tweaked my training and preprocessing to accommodate for a better score overall, but I was so busy with training afterwards that I forgot they would consider the results of Phase 2.

*"Can the user `smehta` please come up and explain their approach?"*

* I knew I wasn't going to follow up Alex's presentation with something really technical so I decided to do the easy thing - tell them exactly how I did it.

*"I've never used a Message-passing Neural Network and I wanted to see how it works so that was my main motivation in participating in this challenge. My first few tries failed which was when I updated my preprocessing pipeline. The core principle I used to tweak my training parameters was basically what Andrew Ng said in Coursera Machine Learning, Week 4 - 'If you are approaching a minima you need to adjust your number of training steps and learning rate such that you neither overshoot it nor converge too slow.'"*

That, ladies and gentlemen, is what I call machine learning (sarcasm? maybe).


**Stay tuned for more posts about experiences from the two other events that I had the privilege to attend this year - Machine Learning Summer School (Madrid), and the Deep Learning Indaba (South Africa).**

