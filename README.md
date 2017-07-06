# test1

[Foo](#foo)

This experiment shows how to solve the [Vehicle Routing Problem][1] (VRP) using the [Bing Maps API][2] to geo-locate addresses and the [TSP R package][3] to optimize routes. The VRP is a common optimization problem that appears in many business scenarios across many industries, the most common case being cargo delivery.

The left-most R script at the top is there just to hold a zip dataset that contains a sample Power BI[4] Desktop file that can be used to visualize the experiment results.

The main experiment workflow contains 1 Python script and 3 R scripts. The idea is to show how to solve the following problem: Given a list of customers and vendors addresses, what is the optimal route for each vendor?

The first R script is used to sample addresses from the new_york_addresses dataset. It samples 100 values that represents customer addresses and 10 values that represent vendor addresses. If you are going to customize the experiment with your own address list or publish it as a web service, you must use the same data structure as created by the R script and place all vendor addresses at the end of your address list.

The Python script is used to call the Bing Maps API that perform geo-location on your address list. To use it, you need to subscribe for a Bing Maps API key, which can be done by following [this instructions][5]. By default, this script output a fixed set of geo-located addresses. When you have your own Bing Maps API key ready, just follow the instructions inside the script to use it.

The second R script groups the customer address list into n groups using the K-Means algorithm, where n is the number of vendors. Then it assigns each vendor to the closest customer group.

Finally, the third R script uses the [Farthest Insertion Algorithm][6] from the R TSP package to compute the optimal route for each address group. This exemplifies a very basic usage scenario, where the objective to be optimized depends only on the distance computed between locations. Here we use Manhattan distance. Perhaps a more reasonable approach would be to use the navigation distance that could also be obtained from the Bing Maps API, which would incorporate street plans constraints. Other more sophisticated approaches could also incorporate time constraints due to traffic conditions, which can also be obtained from the Bin Maps API.

[1]:https://en.wikipedia.org/wiki/Vehicle_routing_problem
[2]:https://msdn.microsoft.com/en-us/library/ff428643.aspx
[3]:https://cran.r-project.org/web/packages/TSP/index.html
[4]:https://powerbi.microsoft.com/en-us/
[5]:https://blogs.bing.com/maps/2015/07/14/bing-maps-now-on-azure/
[6]:https://en.wikipedia.org/wiki/Farthest-first_traversal





# Foo
