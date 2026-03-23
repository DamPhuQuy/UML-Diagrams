### 3.1. Sequence Diagram Notation

#### 3.1.1. Actor

- Represents a role played by an entity interacting externally with a system (subject).
- Can be a human, hardware, or another system.
- Not tied to a specific entity; one person can play multiple actors, and an actor can be played by multiple people.

<p align="center">
    <img src="images/sqactor.png">
</p>

#### 3.1.2. Lifeline

- Represents an individual participant in an interaction.

<p align="center">
    <img src="images/sqlifeline.png">
</p>

#### 3.1.3. Activations

- Thin rectangles on a lifeline showing the time period an element performs an operation.

<p align="center">
    <img src="images/sqactivation.png">
</p>

#### 3.1.4. Messages (communications between lifelines)

- Call Message: Invokes an operation on the target lifeline.

<p align="center">
    <img src="images/sqcall-message.png">
</p>

- Return Message: Sends information back to the caller of a previous message.

<p align="center">
    <img src="images/sqreturn-message.png">
</p>

- Self Message: Invokes a message on the same lifeline.

<p align="center">
    <img src="images/sqself-message.png">
</p>

- Recursive Message: Invokes a message on the same lifeline on top of the current activation.

<p align="center">
    <img src="images/sqrecursive-message.png">
</p>

- Create Message: Instantiates a target lifeline.

<p align="center">
    <img src="images/sqcreate-message.png">
</p>

- Destroy Message: Requests destruction of a target lifeline.

<p align="center">
    <img src="images/sqdestroy-message.png">
</p>

- Duration Message: Shows the time interval between two instants of message invocation.

<p align="center">
    <img src="images/sqduration-message.png">
</p>

#### 3.1.5. Note

- Allows adding comments to elements.
- No semantic effect; purely informative for modelers.

<p align="center">
    <img src="images/sqnote.png">
</p>

### 3.2. Message and Focus of Control

Event:

- Any point in an interaction where **something occurs**.

Focus of Control (Execution Occurrence):

- Shown as a tall, thin rectangle on a lifeline.
- Represents the period during which an **element performs an operation.**
- The **top** aligns with the start of the operation, and the **bottom** aligns with the completion.

Essentially, the focus of control visually shows when a **lifeline is actively doing something**, while an event marks a specific occurrence in the interaction.

<p align="center">
    <img src="images/sqmessage-and-focus-of-control.png">
</p>

### 3.3. Sequence Fragments

| **Operator** | **Fragment Type / Meaning**                                                                                |
| ------------ | ---------------------------------------------------------------------------------------------------------- |
| **alt**      | Alternative: only the fragment whose condition is true will execute.                                       |
| **opt**      | Optional: executes only if the condition is true (like an `alt` with a single branch).                     |
| **par**      | Parallel: fragments run concurrently.                                                                      |
| **loop**     | Loop: fragment may execute multiple times; guard indicates iteration criteria.                             |
| **region**   | Critical region: only**one thread** can execute the fragment at a time.                                    |
| **neg**      | Negative: shows an**invalid interaction**.                                                                 |
| **ref**      | Reference: refers to an interaction defined in another diagram; can include parameters and a return value. |
| **sd**       | Sequence diagram frame: surrounds an**entire sequence diagram**.                                           |

<p align="center">
    <img src="images/fragment.png">
</p>
