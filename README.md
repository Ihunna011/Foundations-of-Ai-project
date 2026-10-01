# AI Route Finder — Dijkstra’s Algorithm

A Python route-finding project developed for Foundations of AI coursework. It uses Dijkstra’s algorithm to find the lowest-cost route between two locations in a simulated road network.

The notebook prints each search step, making it possible to follow how the algorithm explores locations, updates costs and reconstructs the final route.

## Features

- Choose a start and destination from 12 locations.
- Validate location names before starting the search.
- Find the lowest-cost route using a priority queue.
- Display neighbour checks and distance updates.
- Reconstruct the route using predecessor records.
- Report the final path and total cost.
- Represent directional roads and exclude blocked connections.

## Technologies

- Python 3
- `heapq` from the Python standard library
- Google Colab / Jupyter Notebook

No additional Python packages are required.

## Road Network

The network is represented as a weighted adjacency dictionary:

- **Nodes** represent locations.
- **Edges** represent available road connections.
- **Weights** represent travel costs.
- A reverse connection must be explicitly included for a road to work in both directions.

Locations include the Hospital, Town Square, University, Park, College, restaurants, accommodation and other local facilities.

The direct connection from University to Hospital is intentionally excluded to represent a blocked road. The algorithm must find an alternative route.

## How the Algorithm Works

1. Set the start location’s distance to zero and all other distances to infinity.
2. Add the start location to a minimum-priority queue.
3. Remove the queued location with the lowest accumulated cost.
4. Examine its outgoing connections.
5. Update a neighbour’s distance and predecessor when a cheaper route is found.
6. Continue until the destination is removed from the queue or the queue becomes empty.
7. Follow predecessor records backwards to reconstruct the route.

Dijkstra’s algorithm is suitable for this network because all edge weights are non-negative.

## Running the Notebook

1. Download the `.ipynb` notebook from this repository.
2. Open it in Google Colab or Jupyter Notebook.
3. Run the first cell to define the road network.
4. Run the second cell to define the functions and launch the route finder.
5. Enter a start location and destination when prompted.

Location names are case-sensitive and must match the displayed names. Leading and trailing spaces are removed automatically.

To search again, rerun the second cell.

## Example

Input:

    Enter your START location: Park
    Enter your GOAL location: Hospital

Result:

    Final path: Park → Primary & Nursery → Town Square → Hospital
    Total cost: 13

The route cost is calculated as:

    Park → Primary & Nursery: 1
    Primary & Nursery → Town Square: 7
    Town Square → Hospital: 5

    Total: 1 + 7 + 5 = 13

## Coursework and Learning

The project explores graph search in a simulated routing environment with fixed connections and known costs.

Key learning areas include:

- Representing a road network using a weighted directed graph.
- Implementing Dijkstra’s algorithm.
- Using a heap-based priority queue.
- Tracking distances and predecessors.
- Reconstructing a path after a search.
- Validating user input.
- Understanding how blocked roads affect available routes.

## Limitations

- The network and travel costs are manually defined.
- The system does not use live traffic, maps or GPS data.
- Negative edge weights are not supported.
- If the graph is changed so a destination becomes unreachable, the current implementation returns an infinite cost and a path containing only the destination. Explicit “no route found” handling is a future improvement.
- Older priority-queue entries are not skipped, which can cause unnecessary processing.
- This is an educational simulation and is not intended for real emergency navigation.

## Potential Improvements

- Add explicit handling for unreachable destinations.
- Skip outdated priority-queue entries.
- Allow case-insensitive location input.
- Add automated tests for route costs, invalid input and disconnected networks.
- Visualise the network and highlight the selected route.
- Allow road closures and travel costs to be updated.
- Compare Dijkstra’s algorithm with A* using an appropriate heuristic.
