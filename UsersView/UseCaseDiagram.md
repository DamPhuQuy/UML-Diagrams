## 2. Use Case Diagram

- Represent the functionalitites of the system through user interactions
- Shows how users (actors) interact with the system.
- Focus: What the system does (functional requirements), not how it does it.

<p align="center">
    <img src="images/use-case-diagram-annotated.png">
</p>

### 2.0. Determining user's characteristics

- What are their goals?
- How will they use the software?
- What is their level of computer literacy?
- What are their psychological characteristics?
- What are their habits?

### 2.1. Key elements

- `Actor`: external entity (user, another system).
- `Use Case`: functionality (action) the system provides, summary of a use case.
- `System boundary`: a box representing the system itself.
- `Relationships`:
  - `Association` (actor ↔ use case).
  - `«include»` (one use case always uses another).
  - `«extend»` (optional extension).

<p align="center">
    <img src="./images/use-case-key.png">
</p>

#### 2.1.1. Actor

- Someone interacts with use case (system function).
- Named by noun.
- Actor plays a role in the business
- Similar to the concept of user, but a user can play different roles
- For example:
  - A prof. can be instructor and also researcher
  - plays 2 roles with two systems
- Actor triggers use case(s).
- Actor has a responsibility toward the system (inputs), and Actor has expectations from the system (outputs).

<p align="center">
    <img src="images/actor.png">
</p>

#### 2.1.2. Use Case

- A use case needs to describe the interaction between the actor and the system, not the operations that the system should perform.
- System function (process - automated or manual)
- Named by verb + Noun (or Noun Phrase).
- E.g: Some possible use cases
  - Make a reservation
  - Cancel a reservation
  - Change a reservation

- Each Actor must be linked to a use case, while some use cases may not be linked to actors.
- **Objectives** and **interactions**:
  - **Objective**: what the actor wants to achieve.
  - **Interactions**: the steps the actor takes to achieve the objective.

- Example:
  - **Objective**: define the document style
  - **Interactions**: choose the font, choose sizes, choose the page layout, ...

<p align="center">
    <img src="images/usecasebox.png">
</p>

#### 2.1.3. Communication Link

<p align="center">
    <img src="images/communication-links-use-case-diagram.png">
</p>

##### a, Association

- Actor ↔ Use Case connection (solid line).
- Shows communication between the actor and the system (sending/receiving messages).

##### b, Extends

- Optional/conditional behavior.
- Child use case extends the functionality of a base use case.
- Shown with a dashed arrow pointing to the base use case.
- Example: Login ← «extend» Invalid Password.

##### c, Include

- Mandatory reuse of functionality.
- Base use case always includes another use case as part of its flow.
- Shown with a dashed arrow pointing to the included (child) use case.
- Example: Checkout → «include» Payment Processing.

##### d, Generalization (or Inheritance)

- Parent-child relationship between use cases.
- Child use case is a specialized/enhanced version of the parent.
- Shown with a solid line and a hollow triangle pointing to the parent use case.

**Quick memory aid:**

- Association → actor communicates with use case.
- Extend → sometimes adds behavior.
- Include → always reuses behavior.
- Generalization → specialization of another use case.

#### 2.1.4. Boundary of system (or Boundary system)

- The system boundary represents what is inside (system functionality) vs. outside (actors).
- It usually covers the entire system as defined in the requirements.
- For large/complex systems, each module can be treated as its own system boundary.
- Example: In an ERP system, modules like Personnel, Payroll, Accounting each have their own boundary.
- The overall system boundary can also encompass all modules together to show the full system.

<p align="center">
    <img src="images/system-boundary.png">
</p>

### 2.2. How to Identify Actor

Often, people find it easiest to start the requirements elicitation process by identifying the actors. The following questions can help you identify the actors of your system (Schneider and Winters - 1998):

- Who uses the system?
- Who installs the system?
- Who starts up the system?
- Who maintains the system?
- Who shuts down the system?
- What other systems use this system?
- Who gets information from this system?
- Who provides information to the system?
- Does anything happen automatically at a present time?

### 2.3. How to Identify Use Cases?

Identifying the Use Cases, and then the scenario-based elicitation process carries on by asking what externally visible, observable value that each actor desires. The following questions can be asked to identify use cases, once your actors have been identified (Schneider and Winters - 1998):

- What functions will the actor want from the system?
- Does the system store information? What actors will create, read, update or delete this information?
- Does the system need to notify an actor about changes in the internal state?
- Are there any external events the system must know about? What actor informs the system of those events?

### 2.4. Use Case Examples

**Use Case Example - Association Link**

<p align="center">
    <img src="images/use-case-diagram-example.png">
</p>

```java
    // Actor: Student
    class Student {
        private String name;

        public Student(String name) {
            this.name = name;
        }

        // Student interacts with the system by borrowing a book
        public void borrowBook(Library library, String bookTitle) {
            library.borrowBook(this, bookTitle);
        }

        public String getName() {
            return name;
        }
    }

    // System: Library
    class Library {
        // Borrow Books Use Case
        public void borrowBook(Student student, String bookTitle) {
            System.out.println(student.getName() + " borrowed the book: " + bookTitle);
        }
    }

    // Main program to simulate the Use Case
    public class UseCaseDemo {
        public static void main(String[] args) {
            Student student = new Student("Alice");
            Library library = new Library();

            // Interaction (Use Case: Borrow Books)
            student.borrowBook(library, "Design Patterns in Java");
        }
    }
```

**Use Case Example - Include Relationship**

<p align="center">
    <img src="images/include-example.png">
</p>

```java
    // Actor: Student
    class Student {
        private String name;

        public Student(String name) {
            this.name = name;
        }

        // Student triggers the borrow books use case
        public void borrowBook(Library library, String bookTitle) {
            library.borrowBook(this, bookTitle);
        }

        public String getName() {
            return name;
        }
    }

    // System Boundary: Library
    class Library {

        // Main use case: Borrow Books
        public void borrowBook(Student student, String bookTitle) {
            System.out.println(student.getName() + " wants to borrow: " + bookTitle);

            // <<include>> Check Reserved Book
            if (checkReservedBook(bookTitle)) {
                System.out.println("Book is reserved. Borrowing not allowed.");
                return;
            }

            // <<include>> Check Fine
            if (checkFine(student)) {
                System.out.println("Outstanding fine exists. Borrowing not allowed.");
                return;
            }

            System.out.println(student.getName() + " successfully borrowed: " + bookTitle);
        }

        // Included use case: Check Reserved Book
        private boolean checkReservedBook(String bookTitle) {
            // Simulate reserved book logic
            return "Design Patterns in Java".equalsIgnoreCase(bookTitle);
        }

        // Included use case: Check Fine
        private boolean checkFine(Student student) {
            // Simulate fine checking logic
            return student.getName().equalsIgnoreCase("Alice"); // Example: Alice has fines
        }
    }

    // Demo program
    public class UseCaseDemo {
        public static void main(String[] args) {
            Library library = new Library();

            Student student1 = new Student("Alice");
            Student student2 = new Student("Bob");

            // Alice tries to borrow a book but has a fine
            student1.borrowBook(library, "Clean Code");

            System.out.println();

            // Bob tries to borrow a reserved book
            student2.borrowBook(library, "Design Patterns in Java");

            System.out.println();

            // Bob borrows a normal book
            student2.borrowBook(library, "Effective Java");
        }
    }
```

**Extend - Relationship**

<p align="center">
    <img src="images/extend-example.png">
</p>

```java
    // Actor: Student
    class Student {
        private String name;

        public Student(String name) {
            this.name = name;
        }

        // Main Use Case: Request a Book
        public void requestBook(LibrarySystem library, String bookTitle) {
            System.out.println(name + " is requesting the book: " + bookTitle);
            library.requestBook(bookTitle);
        }
    }

    // System Boundary (Library System)
    class LibrarySystem {

        // Main Use Case: Request a Book
        public void requestBook(String bookTitle) {
            System.out.println("Processing request for: " + bookTitle);

            // <<extend>> : Search
            if (!isBookAvailable(bookTitle)) {
                search(bookTitle);  // Extension happens only if condition is met
            }
        }

        // Extension Point: Search
        private void search(String bookTitle) {
            System.out.println("Searching for the book: " + bookTitle);
            // simulate database lookup
            System.out.println("Book not available in current inventory.");
        }

        private boolean isBookAvailable(String bookTitle) {
            // Hardcoded for example; real system would query DB
            return bookTitle.equalsIgnoreCase("Java Programming");
        }
    }

    // Main Program
    public class UseCaseExtendDemo {
        public static void main(String[] args) {
            LibrarySystem library = new LibrarySystem();
            Student student = new Student("Alice");

            // Case 1: Book available
            student.requestBook(library, "Java Programming");

            System.out.println("---------------------------");

            // Case 2: Book not available → triggers <<extend>> Search
            student.requestBook(library, "Design Patterns");
        }
    }
```

**Use Case Example - Generalization Relationship**

<p align="center">
    <img src="images/generalization-example.png">
</p>

```java
    // Base Use Case: Search
    abstract class Search {
        protected String query;

        public Search(String query) {
            this.query = query;
        }

        // General behavior
        public abstract void execute();
    }

    // Specialized Use Case: Search by Call Number
    class SearchByCallNumber extends Search {
        public SearchByCallNumber(String callNumber) {
            super(callNumber);
        }

        @Override
        public void execute() {
            System.out.println("Searching by Call Number: " + query);
            // Simulate database search
            System.out.println("Book found with call number " + query);
        }
    }

    // Specialized Use Case: Search by Author
    class SearchByAuthor extends Search {
        public SearchByAuthor(String authorName) {
            super(authorName);
        }

        @Override
        public void execute() {
            System.out.println("Searching by Author: " + query);
            // Simulate database search
            System.out.println("Books found by author " + query);
        }
    }

    // Main Program
    public class SearchDemo {
        public static void main(String[] args) {
            Search search1 = new SearchByCallNumber("QA76.73.J38");
            search1.execute();

            System.out.println("---------------------");

            Search search2 = new SearchByAuthor("Robert Martin");
            search2.execute();
        }
    }
```

### 2.5. Use Case Diagram - Vehicle Sales Systems

<p align="center">
    <img src="images/example-vehicle-sales-systems.png">
</p>

## 3. Sequence Diagram

<p align="center">
    <img src="images/sqsequence-diagram-example.png">
</p>

**Purpose of Sequence Diagram**

- Models high-level interactions between active objects in a system.
- Shows interactions between object instances in a collaboration that realizes a use case or operation.
- Can depict:
  - Generic interactions: all possible paths.
  - Specific interactions: a single path.

**Object Dimension**

- The horizontal axis shows the elements that are involved in the interaction
- Conventionally, the objects involved in the operation are listed from left to right according to when they take part in the message sequence. However, the elements on the horizontal axis may appear in any order

**Time Dimension**

- The vertical axis represents time proceedings (or progressing) down the page.


