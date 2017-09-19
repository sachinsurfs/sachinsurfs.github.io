---
layout: post
title:  "Let's simulate a cricket match!"
description: A project to predict the results of a match given any set of players on either teams with a little help from Web Scrapers, Big Data and Probability
date:   2016-09-13 10:50:00 +0530
categories: project
author: sachin
---

The problem statement is simple, Given a list of cricketers on two teams, compute the average score expected when they play against each other. Clearly, the first step in the solution is to predict the output for each ball when one player(bowler) bowls against another player(batsman) which requires a probability distribution over every possible outcome(Score:1,2,3,4,6,Out, No Ball, Wide). Once we have this, a simulation would involve computing the overall score from the result of every ball prediction and deciding a winner.

There are two approaches I have followed for this. Each method relies on data extracted from [CricInfo](http://www.espncricinfo.com)

### Naive Method
Our most basic intutition would be to find the outcome of every ball ever played by a player against another player. Then the problem would be simply to compute the probability of one outcome from all outcomes. For instance, 

If M.S.Dhoni(Batsman) has played 20 balls against Shoib Akhtar(Bowler), and if this is the outcome of the 20 balls - [4,4,1,0,2,6,1,1,Out,Wide,2,6,4,1,4,2,Wide,0,0] ,
Then the probability of a 4 would simply be = (No of times 4 occured)/(No of balls)  = 4/20 = 0.2 i.e 20%
Similarly we can calculate the probability of other outcomes and simulate a game between these 2 using the probability distribution.

In order to do this, we need to extract runs data from matches. Then create a player profile for each player. Here is a dataset I extracted from the IPL series - [https://github.com/sachinsurfs/cricket-match-simulation/blob/master/ipl_datasets.tar.gz]

The obvious problem with this method is that there will always be a pair of players that haven't played against each other. 

### Cluster Method

We can patch the problem of missing data in the previous method by finding a pattern between player A who has not bowled against player B, and player C who has bowled against player B. Then we would have an approximated probability distribution for player A vs player B. 

I do this, achieved this by clustering all players to buckets of 10 (I will post another article on how I used Apache Mahout to do this clustering)



### Results

I tested my new clustered player set by simulating historic matches and comparing the results with the actual results. Here is the result of a match between

<Insert JPEG>


 Once we have the cricket score 


(http://www.espncricinfo.com/ci/content/player/index.html)
