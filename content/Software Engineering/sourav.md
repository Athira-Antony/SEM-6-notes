
![[Pasted image 20260213074312.png]]

![[Pasted image 20260213074431.png]]
![[Pasted image 20260213075124.png]]


## Why use association instead of Inheritance?

One of the golden rules in modern software engineering is: **"Favor association over inheritance."**
- **Flexibility:** You can change the associated object at runtime.
- **Low Coupling:** Classes remain more independent, making your code easier to test and maintain.
- **Realism:** Not everything is an "is-a" relationship. A `Car` isn't an `Engine`, it _has_ an `Engine`.

![[Pasted image 20260215074259.png]]
![[Pasted image 20260215113430.png]]

## 🔹Aggregation (code)

- Objects passed from outside.
- Can exist independently.    

Example:
```
Address addr = new Address(); Person p = new Person(addr);
```
## 🔹 Composition

- Object created inside the class.
- Strong life cycle dependency.

Example:
```
class Person {     private Address address = new Address(); }
```


![[Pasted image 20260213075536.png]]

#### A class can have several attributes
- Class
- Attribute
### Relationship:
✅ **Composition**
Reason:
- Attributes do not exist without the class.
- Strong whole–part relationship.

#### A relation can be association or generalisation
Classes:
- Relation
- Association
- Generalisation
### Relationship:
✅ **Inheritance**
Reason:  
Association and Generalisation are types of Relation.

![[Pasted image 20260215134402.png]]

![[Pasted image 20260215134514.png]]


---

> [!NOTE] Facade Design pattern
> Facade forwards each request to the appropriate subsystem object(s).
> Promotes **Low Coupling** ; clients need to know only about facade

---
### Object adapter

> 
>// 1. The Target Interface (What the client expects) 
> interface ModernRect {
>     double getArea(double width, double height);
> }
> 
> // 2. The Adaptee (The old class with incompatible method)
> class LegacyRect {
>     public double calculateArea(double w, double h) {
>         return w * h;
>     }
> }
> 
> // 3. ===The **Object Adapter** (Implements Target, contains Adaptee) ===
> class RectAdapter implements ModernRect {
>     private LegacyRect legacyRect = new LegacyRect(); // Aggregation/Composition
> 
>     @Override
>     public double getArea(double width, double height) {
>         // Adapting the call to the old method
>         return legacyRect.calculateArea(width, height);
>     }
> }
> // ===The **class Adapter** 'is-a' LegacyRect AND 'is-a' ModernRect ===
 class ClassRectAdapter extends LegacyRect implements ModernRect {
>     
>     @Override
>     public double getArea(double width, double height) {
>         // We call the inherited method directly
>         return calculateArea(width, height);
>     }
> }


| **Feature**          | **Object Adapter (Composition)**                    | **Class Adapter (Inheritance)**                     |
| -------------------- | --------------------------------------------------- | --------------------------------------------------- |
| **Adaptability**     | Can adapt a class **and all its subclasses**.       | Can only adapt **one specific class**.              |
| **Logic**            | One adapter works for an entire family of objects.  | You need a new adapter for every specific subclass. |
| Relationship         | Represents a "has-a" aggregation                    | Represents an "is-a" inheritance relationship       |
| **Feature**          | **object  Adapter(loose)**                          | **Class Adapter (Tight)**                           |
| **Binding**          | Runtime(composition)                                | Compile-time (Inheritance).                         |
| **Visibility**       | Adapter only sees public members of Adaptee.        | Adapter sees all protected members of Adaptee.      |
| **Impact of Change** | Changes in Adaptee are isolated within the Adapter. | Changes in Adaptee can break the Adapter easily.    |

---
## Difference between comparator and comparable in java

-  Think of **Comparable** as the "default" way an object sorts itself. A class implements this interface when there is one obvious, natural way to order its instances (like ID number or Alphabetical name).
- Think of **Comparator** as an "external" sorting tool. You use this when you want to sort objects in different ways (e.g., once by name, another time by grade) without changing the original class code.

| **Feature**        | **Comparable**                        | **Comparator**                                    |
| ------------------ | ------------------------------------- | ------------------------------------------------- |
| **Definition**     | "I can compare myself to another."    | "I am an external tool that compares two others." |
| **Method**         | `public int compareTo(T obj)`         | `public int compare(T obj1, T obj2)`              |
| **Package**        | `java.lang` (No import needed)        | `java.util` (Must import)                         |
| **Logic Location** | Inside the actual class being sorted. | In a separate class (or anonymous/lambda).        |
| **Usage**          | Collections.sort(list)                | Collections.sort(list, new MyComparator())`       |

---

### Observer Design pattern

![[Pasted image 20260213084746.png]]

> [!NOTE]
> - Subject represents actual state , where observers represent different views of the state.


