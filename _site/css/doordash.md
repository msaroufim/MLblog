Have to go down a huge list before I can get to appstore link
Why am I even seeing closed restaurants? I don't need a popup for every open restaurant

# Categorization and Recommendation

* Can have buckets for different types of cuisine or buckets via type range (yelp, reviews?)
* Recommend restaurants that people liked, rating system
* Friends can recommend you pick something up
* Friends can take takeout for their friends
* Let tip be standardized


# Dispatching

* Pricing model for drivers is it based on demand?
* Look at historical data to see when most demand is needed

# Scheduling

* Shortest path from driver location to restaurant to customer (trivial solution)
* Batch orders together
* freshness = 1/t where t is time > 0
* Want to optimize alpha* \sum_{orders} cost(order_i) + beta* (1/t) * number of orders where cost(order) = d(driver,restaurant,customer)
* Can set up a bunch of different cost functions and see which ones perform best 
* Can experiment on different markets
* Current is by region I assume? Only allocate drivers to certain regions
* Pizza Hut back home had an oven as a bag so similar idea could be adapted to get a larger supply of drivers

# Web Development

* Backend in Django, running into performance issues?
* New relic for analytics: why did you choose that?
