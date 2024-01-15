# cs50_artificial_intelligence
Lesson programs, quizzes and projects on Introduction to Artificial Intelligence with Python from Harvard's CS50AI course.


# Search

### Terminology

 **Agent:** entity that perceives its environment and acts upon that enviroment.

**State:** a configuration of the agent and its environment.

*initial state ->* the state in which the agent begins.

**Actions:** choices that can be made in a state.

`ACTIONS(s)` -> returns the set of actions that can be executed in state s.

**Transition Model:** a description of what state results from performing any applicable action in any state.

`RESULT(s,a)` -> returns the state resulting from performing action a in state s. 

**State Space:** the set of all states reachable from the initial state by any sequence of actions.

**Goal Test:** way to determine whether a given state is a goal state.

**Path Cost:** numerical cost associated with a given path.

## Search Problem

- Initial State;
- Actions;
- Transition Model;
- Goal Test;
- Path Cost Function;

**Solution:** A sequence of actions that leads from the initial state to a goal state.

*optimal solution* -> a solution that has the lowest path cost among all solutions.

**Node:** a data structure that keeps track of 

- a state;
- a parent (node that generated this node);
- an action (action applied to parent to get node);
- a path cost (from initial state to node);

### Approach

- Start with a frontier that contains the initial state.
- Start with an empty explored set.
- Repeat: 
    - If the frontier is empty, then no solution.
    - Remove a node from the frontier.
    - If node contains goal state, return the solution.
    - Add the node to the explored set.
    - Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set.

## Uninformed Search

Search strategy that uses no problem-specific knowledge.

### Depth-First Search

Search algorithm that always expands the deepest node in the frontier.

**Stack:** last-in first-out in data type.

### Breadth-First Search

Search algorithm that always expands the shallowest node in the frontier.

**Queue:** first-in first-out data type.

## Informed Search

Search strategy tha uses problem-specific knowledge to find solutions more efficiently.

### Greedy Best-First Search

Search algorithm that expands the node that is closest to the goal, as estimated by a heuristic function *h(n)*.

### A* Search

Search algorithm that expands node with lowest value of *g(n) + h(n)*.

    *g(n)* = cost to reach node

    *h(n)* = estimated cost to goal

optimal if:

- *h(n)* is admissible (never overestimates the true cost)
- *h(n)* is consistent (for every node *n* and sucessor *n'* with step cost *c*, *h(n) <= h(n') + c*)

## Adversarial Search

### Minmax

- MAX aims to maximize score.
- MIN aims to minimize score.

Game:
- *s0*: initial state.
- *PLAYER(s)*: returns which player to move in state *s*.
- *ACTIONS(s)*: returns legal moves in state *s*.
- *RESULT(s,a)*: returns state after action *a* taken in state *s*.
- *TERMINAL(s)*: checks if state *s* is a terminal state.
- *UTLITY(s)*: final numerical value for terminal state *s*.