# Scalability
Even if a system is working fine today, that doesn't mean it will necessarily work reliably in the future. One common reason for system degradation is increasing load.

Scalability is the term we use to describe a system's ability to cope with increased load. The question to be addressed is how the system will cope with future changes in the environment.

## Describing Load
To have a discussion on growth, we need to describe the load the system is experiencing. *Load* can be described with a few numbers which we call *load parameters*. The best choice of parameters depend on the system - it can be request per second for web server, ratio of reads to writes in a database, number of simultaneously active user in the chat room...

### Twitter as an example
Two of twitter's main operations are

*Post tweet* - a user can publish a new message to their followers (over 12000 requests/second at peak)

*Home Timeline*  - a user can view tweets posted by the people they follow (300,000 requests/second)

The twitter challenge lies in its *fan-out* operation - each user follows many people. and each user is followed by many people. There are two ways of implementing these two operations.

**Approach 1** - Posting a tweet inserts a new tweet into the global collection of tweets, when a user requests their home timeline, look up all the people they follow, find all the tweets for each of those users and merge them

**Approach 2** - Maintain a home timeline cache for each user, and whenever someone posts a tweet, look up all the follower, this tweet is sent to all the home timeline cache of their followers.

Approach 1 struggled to keep up when twitter grew large. Approach 2 is then implemented - the bulk of the work is done during write  and less during read.

However, the average case does not apply to accounts with huge number of followings - for example, for a celebrity with 30 million followers would require 30 million writes to home timeline for every tweet.

The final twist is a hybrid of two approaches. The underlying cache implementation is supported by an edge case system which allow home timeline to separately query tweets from any celebrity an user follows.

## Describing Performance
After choosing a key load parameter, the next step is to investigate what happens when the load increases - there are two ways to look at it

1. Given increased load parameter and same system resource, how is the performance affected

2. Given increased load parameter, how much more system resources is required to keep performance unchanged.

Similar to describing load, we need numbers to describe the **performance** of a system. For batch processing system, throughput is often used. For web servers, response is used.

For an online system handling larger number of requests, the response time can vary a lot between requests, we therefore need to think about response time as a *distribution* rather than single numbers.

In a distribution of responses, the arithmetic mean doesn't really provide much insight. Instead, the median gives us a clearer picture of how our system is performing. For example, if the median of the requests is 200ms, then half of the requests take more than 200ms to respond.

In order to figure out bad the outliers are, we should focus more on the higher percentiles, the *95th, 99th and 99.9th* are common. They are the response time thresholds at which 95%, 99% and 99.9% requests are faster than that threshold.

High percentiles of response times, also known as *tail latency*, are important because they directly affect users' experience. In general, improving the 99p and 99.9p leads to a improvement in customer satisfaction. On the other hand, optimizing for the 99.99 percentile is deemed too expensive and difficult, because they are often the result of events outside of our control.

### Queuing Delay
Queuing delays often account for a large part of the response time at high percentiles. As servers can only process a small number of things in parallel, it only takes a small number of slow requests to hold up the processing of subsequent requests - this effect is known as *head of line blocking*. 

Even if the subsequent requests are fast, the client will experience long wait time due to the queuing delay. Therefore, it is important to **measure response times on the client side**.

---
##### TLDR
1. Find suitable load parameters, typical ones are throughput and requests per second
2. Find suitable performance metrics, typical ones are request response time.
3. For response time, it is often more meaningful to look at median and higher percentiles (also known as *tail latency*)
4. It is more accurate to measure response time on client side
---

## Percentiles in Practice 
High percentiles become especially important in backend services that are called multiple times as part of serving a single end-user request. Even only if a small percentage of backend calls are slow, the change of getting slow call increases if an end-user request requires multiple backend calls.

If we want to add response time percentile to the monitoring dashboards, we need to efficiently calculate them on the ongoing basis.

For example, have a rolling window of response time of requests in the last 10 minutes, every minute, compute the median and various percentiles over the values in the window.

Some existing tools are - [[T-digest]], [[Forward Decay]], [[HDR Histogram]].

## Scaling - Coping with increased load