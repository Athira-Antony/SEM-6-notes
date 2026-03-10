### What is a model?

A **model** is a **simplified representation of a real system, object, or process**, used to understand, analyse, or explain how the real system works.
It shows the **important features** of a system while ignoring unnecessary details.
✅ Example: A map is a model of a real place.

### **2. Why develop a model? How does constructing a model help?**

Developing a model helps because :
- It makes **complex systems easier to understand
- Helps in **visualising the system before implementation**
- Identifies **errors or missing requirements early**
- Improves **communication** among developers and users
- Saves **time and cost** by reducing mistakes
- Helps in **analysis and decision making**

### **3. Give some examples of models**

Examples include:
- **Flowcharts**
- **UML diagrams** (Use case diagram, Class diagram)
- **Data Flow Diagrams (DFD)**
- **ER diagrams**
- **Prototype models**
- **Mathematical models**
- **Architectural models**


> [!NOTE]  ## What is **Exploratory Style**?
> **Exploratory style (or Exploratory development)** is a **software development approach** where:
> 
> - Requirements are **not completely known at the beginning**
>     
> - Development and requirement discovery happen **together**
>     
> - Developers **experiment, try ideas, modify, and improve** continuously
>     
> 
> 👉 The system evolves through exploration.


![[Pasted image 20260212183727.png]]
![[Pasted image 20260216162343.png]]
### **Issues of `goto` statements in control flow**

#### **1. Unstructured control flow**
- Program execution jumps randomly from one place to another.
- The logical flow becomes difficult to follow.
#### **2. Spaghetti code**
- Too many jumps create tangled code.
- The program becomes messy and hard to understand.
#### **3. Difficult debugging**
- Since execution can jump anywhere, finding errors becomes difficult.
- Tracking program execution is confusing.
#### **4. Poor maintainability**
- Modifying one part may affect unrelated parts.
- New programmers find it hard to understand the code.
#### **5. Hard testing and verification**
- Predicting program paths becomes complex.
- Testing all possible paths is difficult.

### **Why structured programming avoids `goto`**

Structured programming replaces `goto` with:

- **Sequence**
- **Selection** (`if`, `switch`)
- **Iteration** (`for`, `while`)

These make control flow **clear and predictable**.

---

> [!NOTE] ## What is Structured Programming?
> 
> > **Structured programming** is a programming approach in which a program is divided into **small, well-organized modules or functions**, using clear control structures such as **sequence, selection, and iteration**, avoiding unnecessary jumps like `goto`.
>    **Main ideas:**
> - Program divided into modules/functions
> - Logical flow of control
> - Easy to read and understand
> - Improves testing and maintenance
> **Control structures used:**
> - Sequence (statements executed in order)
> - Selection (`if`, `switch`)
> - Iteration (`for`, `while`)

![[Pasted image 20260212184631.png]]

![[Pasted image 20260212203414.png]]

![[Pasted image 20260212203934.png]]

![[Pasted image 20260212204356.png]]

![[Pasted image 20260212205311.png]]

![[Pasted image 20260212205327.png]]

![[Pasted image 20260212205407.png]]

![[Pasted image 20260212214634.png]]
![[Pasted image 20260216192422.png]]

## Requirement Analysis and Specification

---

- Requirement gathering -> fully understand the user requirements
- Requirement Analysis  -> remove inconsistencies , anomalies, incompleteness etc. from requirements
- Requirement Specification -> Document requirements properly in an SRS document
---

> [!NOTE]  SRS document
>  - main aim : systematically organise the requirements  arrived during requirements analysis
>  - document the requirements properly

