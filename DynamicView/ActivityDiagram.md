## 4. Activity Diagram

**What is activity diagram?**

A diagram that represents the workflow or behavior of a system.

- Shows activities, conditions, branching, and concurrency in a process.
- Commonly used to:
  - Describe business processes.
  - Illustrate the flow of a use case or system process.
- Notation: includes action, decision, merge, fork, join, start, end.
- Does not necessarily show detailed computational steps like an algorithm.

<p align="center">
    <img src="images/basic-activity-diagram.png">
</p>

### 4.1. Activity Diagram Notation

#### 4.1.1. Activity

Is used to represent a set of actions

<p align="center">
    <img src="images/1.png">
</p>

#### 4.1.2. Action

A task to be performed

<p align="center">
    <img src="images/2.png">
</p>

#### 4.1.3. Control Flow

Shows the sequence of execution

<p align="center">
    <img src="images/3.png">
</p>

#### 4.1.4. Object Flow

Show the flow of an object from one activity (or action) to another activity (or action).

<p align="center">
    <img src="images/4.png">
</p>

#### 4.1.5. Initial Node

Portrays the beginning of a set of actions or activities

<p align="center">
    <img src="images/5.png">
</p>

#### 4.1.6. Activity Final Node

Stop all control flows and object flows in an activity (or action)

<p align="center">
    <img src="images/6.png">
</p>

#### 4.1.7. Object Node

Represent an object that is connected to a set of Object Flows

<p align="center">
    <img src="images/7.png">
</p>

#### 4.1.8. Decision Node

Represent a test condition to ensure that the control flow or object flow only goes down one path

<p align="center">
    <img src="images/8.png">
</p>

#### 4.1.9. Merge Node

Bring back together different decision paths that were created using a decision-node.

<p align="center">
    <img src="images/9.png">
</p>

#### 4.1.10. Fork Node

Split behavior into a set of parallel or concurrent flows of activities (or actions)

<p align="center">
    <img src="images/10.png">
</p>

#### 4.1.11. Join Node

Bring back together a set of parallel or concurrent flows of activities (or actions).

<p align="center">
    <img src="images/11.png">
</p>

#### 4.1.12. Swimlane and Partition

A way to group activities performed by the same actor on an activity diagram or to group activities in a single thread

<p align="center">
    <img src="images/12.png">
</p>
