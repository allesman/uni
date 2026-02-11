---
tags:
  - tree
  - computer_architecture
domain: E
finished: true
---
--- 
**Date**: 11.02.26
**Time**: 10:25 

> **Brief Summary**
> Steiner Trees can be used to solve the infamous **routing problem** through the use of heuristics.

---
# Steiner Tree

Steiner Trees can be used to easily solve **single-net** routing problems.

Observe a given net of points that we want to connect via a single wire:
![[Pasted image 20260211102754.png|300]]

To find the actual most optimal Steiner Tree is hard, but we can find a good **rectilinear** Steiner Tree which is jut a Steiner Tree that only connects points via **horizontal** and **vertical** segments.

The first step in getting a Steiner Tree is finding all **Hanan Points**. This can be done by drawing **vertical** and **horizontal** lines originating from each point on the grid. The intersections of these lines are called **Hanan Points**.

> The main motivation for studying the Hanan grid stems from the fact that it is known to contain a minimum length [rectilinear Steiner tree](https://en.wikipedia.org/wiki/Rectilinear_Steiner_tree "Rectilinear Steiner tree") for S. It is named after Maurice Hanan, who was first to investigate the rectilinear Steiner minimum tree and introduced this graph.


![[Pasted image 20260211104454.png|300]]

Once we have our **Hanan Grid** we can easily construct a **minimal rectilinear** Steiner Tree by applying a specific algorithm that uses a neat distance-based heuristic. The algorithm functions as follows:

**Initial Step**
1) Pick a point that has the smallest distance to the next closest point, if two or more are found with equal distances to the next closest point then pick the **leftmost** one.
**Recursive Step**
2) Construct a **Minimal Bounding Box** from the initial point to the next closest point. The path side of the box which is **closest** to another point in the grid is chosen. If both sides are equidistant from two separate points then either can be picked.
3) The point that has been pathed to becomes your new starting point, repeat step 2 recursively until there are no more points.

![[Pasted image 20260211104651.png]]

**Finding Steiner Points**

→ For p Nodes there is a maximum of ($p^2 - p$) candidates for Steiner Points.

A hanan point that is an intersection of a horizontal and vertical line is considered a Steiner Point. However our goal is often to find the **maximal** Steiner Points, whcih are the Steiner Points that connect the most amount of lines. All Steiner Tree points should be connected to the Steiner Points.

![[Screenshot 2026-02-11 at 10.54.53.png|300]]




---
## Related Topics
- [[]]







