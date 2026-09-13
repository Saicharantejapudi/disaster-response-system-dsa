# National Disaster Response & Rescue Navigation System

---

## Project Overview

The **National Disaster Response & Rescue Navigation System** is a graph-based emergency navigation application designed to assist rescue teams during natural disasters such as floods, cyclones, earthquakes, landslides, cloudbursts, and urban flooding. 

The system models India's transportation network as a **weighted graph**, where vertices represent 36 major disaster-prone Indian cities and edges represent road connections with distance weights and safety-balanced hazard ratings.

The project integrates a high-performance **C++ DSA engine** with an **interactive Node.js web dashboard** to simulate real-world emergency response operations. Users can select a source and destination from major disaster-prone locations across India, choose a routing algorithm (Dijkstra, A* Heuristic Search, BFS, or DFS), and visualize the optimal rescue path on an interactive OpenStreetMap layer while locating nearby hospitals, shelters, and rescue teams.

---

## Aim & Objectives

* **Aim**: To develop an intelligent graph-based disaster response system that computes the shortest and safest rescue routes using Data Structures and Algorithms, enabling efficient emergency navigation and resource allocation during disaster situations.
* **Objectives**:
  * Design a weighted graph representing 36 disaster-prone locations across India.
  * Implement graph traversal algorithms (BFS and DFS) for reachability and connectivity analysis.
  * Implement shortest path algorithms (Dijkstra's Algorithm and A* Search).
  * Visualize rescue routes on an interactive map.
  * Locate nearby hospitals, shelters, and rescue teams along the computed path.
  * Demonstrate practical applications of Graph Theory and Data Structures.

---

## Technology Stack

* **Frontend**: HTML5, CSS3, JavaScript (Vanilla), Leaflet.js with OpenStreetMap.
* **Backend**: C++ (DSA Pathfinder Engine), Node.js & Express.js (REST API Layer).
* **Database & File Handling**: CSV File Handling (Coordinates, Roads, and Resources datasets).
* **Tools**: Visual Studio Code, Git & GitHub.

---

## Data Structures Used

* **Graph (Adjacency List)**: Models the sector network efficiently using `std::unordered_map` and adjacency list representations.
* **Vector**: Dynamic array representation used across graph traversals and path listings.
* **Queue**: Powers the level-order BFS traversal logic.
* **Stack**: Powers the depth-first DFS graph search traversal.
* **Priority Queue (Min Heap)**: Powers Dijkstra's and A* search node expansions.
* **Hash Map (`std::unordered_map`)**: Powers coordinates lookup and parents tracking maps.

---

## Algorithms Implemented

### 1. Breadth First Search (BFS)
* **Used for**: Graph traversal, connectivity checking, and reachability analysis.
* **Time Complexity**: `O(V + E)`

### 2. Depth First Search (DFS)
* **Used for**: Graph traversal, graph exploration, and connected component analysis.
* **Time Complexity**: `O(V + E)`

### 3. Dijkstra's Algorithm
* **Used for**: Finding the shortest safety-balanced rescue route on weighted graphs.
* **Time Complexity**: `O(E log V)`

### 4. A* Search Algorithm
* **Used for**: Fastest rescue route calculation using a goal-oriented spatial heuristic calculated via the **Haversine formula**.
* **Time Complexity**: `O(E log V)` (average case)

---

## Proposed Graph Nodes (36 Locations across India)

The graph contains approximately **36 strategically selected locations** that are frequently affected by natural disasters:

* **Flood-Prone Regions**: Chennai, Hyderabad, Bengaluru, Mumbai, Patna, Guwahati, Srinagar, Kochi.
* **Cyclone-Prone Coastal Cities**: Visakhapatnam, Bhubaneswar, Puri, Paradeep, Kakinada, Vijayawada, Kolkata.
* **Earthquake-Sensitive Zones**: Gangtok, Shillong, Imphal, Itanagar, Dehradun.
* **Landslide-Prone Hill Stations**: Shimla, Manali, Dharamshala, Joshimath, Kedarnath, Nainital, Darjeeling.
* **Cloudburst / Heavy Rainfall Areas**: Leh, Kullu, Mandi, Jammu.
* **Disaster Response & Coordination Hubs**: New Delhi, Lucknow, Nagpur, Pune, Bhopal.

---

## Key Features

1. **Interactive Route Planning**: Select any supported disaster-prone location as the source and destination from dropdown menus or directly by clicking on the map.
2. **Intelligent Route Calculation**: Computes the safety-balanced route using Dijkstra's Algorithm or A* Search, bypassing blocked roads.
3. **Interactive Map**: Displays source, destination, the continuous path polyline, and satellites representing hospitals, shelters, and rescue teams along the path.
4. **Road Blockages Toggles**: Directly click on map roads or toggle road check-boxes in the operations sidebar. Active pathfinders will automatically bypass blocked roads.
5. **Add Resource Portal**: Add new hospitals, shelters, or rescue teams dynamically in real-time. Node.js writes them back to the CSV database, so they are immediately available.
6. **Performance & Comparisons**: Displays execution time, nodes expanded, total distance, and estimated travel time. Shows a side-by-side comparison table of all 4 algorithms.

---

## Getting Started: How to Run the Project

### 1. Prerequisites

Before running the project, ensure you have the following installed on your machine:

* **[Node.js](https://nodejs.org/)** (v16.x or higher recommended) and **npm**.
* *(Optional but Recommended)* **C++ Compiler (`g++` / GCC / MinGW)** with C++11 support or higher.
  > **Note (Dual-Engine Architecture):** If `g++` is not installed on your system, the server will seamlessly run using the **pure JavaScript fallback DSA engine** (`dsaEngine.js`). For maximum speed and performance, compiling the native C++ engine is recommended.

---

### 2. Installation & Quick Start

#### Step 1: Clone the Repository & Navigate to Directory
```bash
git clone https://github.com/<your-username>/disaster-response-system-dsa.git
cd disaster-response-system-dsa
```

#### Step 2: Install Dependencies
Install the required Node.js packages:
```bash
npm install
```

#### Step 3: Build the C++ DSA Engine *(Optional)*
Compile the C++ source files into the native executable:
```bash
npm run build
```
* On **Windows**, this generates `DisasterSystem.exe`.
* On **Linux / macOS**, this generates `DisasterSystem`.

#### Step 4: Start the Server
Launch the Node.js Express server:
```bash
npm start
```
*(Alternatively, you can run `npm run dev` or `node server.js`)*

#### Step 5: Open the Web Application
Open your web browser and navigate to:
```
http://localhost:3000
```

---

### 3. Running Standalone CLI Mode (Direct C++ Engine)

You can also run the C++ engine directly from the command line without launching the web server:

* **Display Graph & Roads:**
  ```bash
  # Windows
  .\DisasterSystem.exe --graph
  # Linux / macOS
  ./DisasterSystem --graph
  ```

* **Calculate Rescue Route (Dijkstra / A* / BFS / DFS):**
  ```bash
  .\DisasterSystem.exe --route "New Delhi" "Mumbai" --algo dijkstra
  .\DisasterSystem.exe --route "Chennai" "Kolkata" --algo astar
  ```

* **Simulate Blocked Roads:**
  ```bash
  .\DisasterSystem.exe --route "New Delhi" "Mumbai" --algo dijkstra --block "New Delhi-Mumbai"
  ```

* **Graph Traversals (BFS / DFS):**
  ```bash
  .\DisasterSystem.exe --traversal bfs "Bengaluru"
  .\DisasterSystem.exe --traversal dfs "Bengaluru"
  ```

* **Query Emergency Resources for a Sector:**
  ```bash
  .\DisasterSystem.exe --resources "Chennai"
  ```

---

### 4. Project Structure

```text
disaster-response-system-dsa/
├── backend/
│   └── src/
│       ├── algorithms.cpp / .h  # Dijkstra, A*, BFS, DFS implementations
│       ├── data.cpp / .h        # CSV data parser and models
│       ├── graph.cpp / .h       # Adjacency list graph representation
│       └── main.cpp             # CLI entry point and JSON output formatter
├── data/
│   ├── coordinates.csv          # Lat/Long for 36 Indian cities
│   ├── disasterData.json        # Disaster statistics & analytics
│   ├── hospitals.csv            # Hospital facilities & bed counts
│   ├── roads.csv                # Graph edges with distances & danger ratings
│   ├── shelters.csv             # Relief shelters & capacities
│   └── teams.csv                # Disaster response units & specialties
├── frontend/
│   ├── index.html               # Main dashboard UI
│   ├── css/                     # Styling and layout
│   └── js/                      # Leaflet map, API integration, and interactions
├── build.js                     # Cross-platform C++ compilation script
├── dsaEngine.js                 # Fallback DSA engine written in Node.js
├── server.js                    # Express API server & static host
└── package.json                 # Project configuration & npm scripts
```
