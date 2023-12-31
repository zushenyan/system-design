# Step 1 - Clarify Requirements

1. Functional features (fundamental features)
   - For example, Facebook users should be able to share posts.
2. Non-functional features
   - For example, the latency of response should not exceed 200ms.
3. Extended features
   - Only if essential features are covered should we discuss extra features.

# Step 2 - Database Design

![data model](./data-model.png)

1. Draw the data models. [dbdiagram.io](https://dbdiagram.io/home)
2. Discuss what kind of database we are going to use (SQL vs NoSQL)

# Step 3 - Estimate

1. Estimate the read/write ratio.
2. Calculate the traffic capacity. (QPS)
3. Calculate the bandwidth capacity.
4. Calculate the storage capacity.
5. Calculate the cache capacity. (with 80-20 rule, only 20% of data is hot and worth caching)

# Step 4 - High Level Design

![blocks](./blocks.png)

Draw block digram to represent the system.

# Step 5 - Detialed Design

Identify bottlenecks and discuss trade-offs.

Possible common questions
1. Consistency vs Availability?
2. Which components need load balancer?
3. What kind of data partitioning we are going to use?
4. Hom many layers of caches do we need?
5. Any single point of failure spotted?

# Optional - Define API Interface

Roughly outline the API the system will be using.
```
post(apiKey, userId, userLocation, content, ...)
```
```
markTweetFavourite(userId, tweetId, timestamp, ...)
```