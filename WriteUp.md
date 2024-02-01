# Motion Planning Project Write Up

## Starter Code Explanation

The starter code is a modification of the `backyard_flyer` script, it's main
difference beeing that there is an additional state phase `PLANNING` and the
corresponding transition callbacks. The added `plan_path` callback loads the
date from `colliders.csv` and plans a path for a point with offset (10, 10) from
the starting point via a simple A-star alogrithm on the grid with only vertical/
horizontal possible motions. The computed waypoints are then communicated via
`send_waypoints`.

## Path Planning Implementation

The path planning is implemented as an A-star search on the Voronoi graph created
from the obstacles. I can't see any obstacles in the simulator sadly, so I
didn't add an additional 5m safety distance. The Bresenham algorithm is used to
check for collisions along a flight path. The closest node of the Voronoi graph
is determined by the minimal Euclidian distance, the end node of the Voronoi
graph is determined analogously.

