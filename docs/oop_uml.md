> The Unified Modeling Language (UML) is a general-purpose, developmental, modeling language in the field of software engineering, that is intended to provide a standard way to visualize the design of a system.

<ul>
<li>http://www.yuml.me/</li>
<li>Use UML with IntellIJ: <a href="https://www.jetbrains.com/idea/features/uml_designer.html">UML Designer</a></li>
</ul>

# Architecture

[^1]

![](http://www.openloop.com/softwareEngineering/uml/overview/archAndUML.jpg)

* **Design** of a system consists of classes, interfaces and collaboration. UML provides class diagram, object diagram to support this.
* **Implementation** defines the components assembled together to make a complete physical system. UML component diagram is used to support implementation perspective.
* **Process** defines the flow of the system. So the same elements as used in Design are also used to support this perspective.
* **Deployment** represents the physical nodes of the system that forms the hardware. UML deployment diagram is used to support this perspective.

# Modelling Types

[^2]

![](http://static2.creately.com/blog/wp-content/uploads/2012/01/UML-Diagram-Types.png)

# Diagrams

## Usecase Diagram

[^3] [^4] [^5]

> A `use case` diagram at its simplest is a **representation of a user's interaction** with the system that shows the **relationship between the user** and the **different use cases** in which the user is involved.

> A use case diagram can identify the different types of users of a system and the different use cases and will often be accompanied by other types of diagrams as well.

[](https://youtu.be/XpqyiBR0lJ4?t=455)

![](http://agilemodeling.com/images/models/useCaseDiagram.jpg)

Use case diagrams depict:

* **Use cases.** A use case describes a sequence of actions that provide something of measurable value to an actor and is drawn as a horizontal ellipse. <small>[(example)](http://www.uml-diagrams.org/use-case.html)</small>
* **Actors.** An actor is a person, organization, or external system that plays a role in one or more interactions with your system. Actors are drawn as stick figures. <small>[(example)](http://www.uml-diagrams.org/use-case-actor.html)</small>
* **Associations.** Associations between actors and use cases are indicated in use case diagrams by solid lines. An association exists whenever an actor is involved with an interaction described by a use case. Associations are modeled as lines connecting use cases and actors to one another, with an optional arrowhead on one end of the line. The arrowhead is often used to indicating the direction of the initial invocation of the relationship or to indicate the primary actor within the use case. The arrowheads are typically confused with data flow and as a result I avoid their use. <small>[(example)](http://www.uml-diagrams.org/use-case-actor-association.html)</small>
* **Extend**: Extend is a directed relationship that specifies how and when the behavior defined in usually supplementary (optional) extending use case can be inserted into the behavior defined in the extended use case. <small>[(example)](http://www.uml-diagrams.org/use-case-extend.html)</small>
* **Include** is a directed relationship between two use cases which is used to show that behavior of the included use case (the addition) is inserted into the behavior of the including (the base) use case. <small>[(example)](http://www.uml-diagrams.org/use-case-include.html)</small>
* **System boundary boxes** (optional). You can draw a rectangle around the use cases, called the system boundary box, to indicates the scope of your system. Anything within the box represents functionality that is in scope and anything outside the box is not. System boundary boxes are rarely used, although on occasion I have used them to identify which use cases will be delivered in each major release of a system. <small>[(example)](http://www.agilemodeling.com/artifacts/useCaseDiagram.htm)</small>
* **Packages** (optional). Packages are UML constructs that enable you to organize model elements (such as use cases) into groups. Packages are depicted as file folders and can be used on any of the UML diagrams, including both use case diagrams and class diagrams. I use packages only when my diagrams become unwieldy, which generally implies they cannot be printed on a single page, to organize a large diagram into smaller ones. <small>[(example)](http://www.agilemodeling.com/artifacts/useCaseDiagram.htm)</small>

## Class Diagram

[^6]

> In software engineering, a class diagram in the Unified Modeling Language (UML) is a type of static structure diagram that describes the structure of a system by showing the system's classes, their attributes, operations (or methods), and the relationships among objects.

![](http://agilemodeling.com/images/models/classDiagramInitial.jpg)

#### 3.3.1 UML Association [^9] [^10]

![](http://www.uml-diagrams.org/association/class-association-overview.png)

**Association**

Association is reference based relationship between two classes. Here a class A holds a class level reference to class B. Association can be represented by a line between these classes with an arrow indicating the navigation direction. In case arrow is on the both sides, association has bidirectional navigation.

![](https://nirajrules.files.wordpress.com/2011/07/association.png?w=630)

**Aggregation**

`Aggregation (shared aggregation)` is a "weak" form of aggregation when part instance is independent of the composite:

* the same (shared) part could be included in several composites, and
* if composite is deleted, shared parts may still exist.

Shared aggregation is shown as binary association decorated with a hollow diamond as a terminal adornment at the aggregate end of the association line. The diamond should be noticeably smaller than the diamond notation for N-ary associations. Shared aggregation is shown as binary association decorated with a hollow diamond.

![](http://lh3.googleusercontent.com/_aUOgqE3fGXc/Sh32cQ4pjVI/AAAAAAAAAaY/2lq7mZumWM8/s1600/image%5B24%5D.png)

**Composition**

Composition (composite aggregation) is a "strong" form of aggregation. Composition requirements/features listed in UML specification are:

* it is a whole/part relationship,
* it is binary association
* part could be included in at most one composite (whole) at a time, and
* if a composite (whole) is deleted, all of its composite parts are "normally" deleted with it.

Note, that UML does not define how, when and specific order in which parts of the composite are created. Also, in some cases a part can be removed from a composite before the composite is deleted, and so is not necessarily deleted as part of the composite.

![](http://lh3.ggpht.com/_aUOgqE3fGXc/Sh35Y1ga0lI/AAAAAAAAAas/9FnQ1sRJObY/image_thumb%5B2%5D.png?imgmax=800)

**Aggregation vs Composition**

[^11]

![](https://atomicobject.com/uploadedImages/archive/images/UML_CompositionAggregation.png)

## Sequence Diagram

[^7]

> A Sequence diagram is an interaction diagram that shows how processes operate with one another and in what order. It is a construct of a Message Sequence Chart.

> A sequence diagram shows object interactions arranged in time sequence.

> It depicts the objects and classes involved in the scenario and the sequence of messages exchanged between the objects needed to carry out the functionality of the scenario. Sequence diagrams are typically associated with use case realizations in the Logical View of the system under development. Sequence diagrams are sometimes called event diagrams or event scenarios.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/CheckEmail.svg/469px-CheckEmail.svg.png)

## Activity Diagram

[^8]

Activity diagrams are graphical representations of workflows of stepwise activities and actions with support for choice, iteration and concurrency. In the Unified Modeling Language, activity diagrams are intended to model both computational and organizational processes (i.e. workflows). Activity diagrams show the overall flow of control.

![](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/uml/activity-diagram/login-activity-diagram-525x471.jpg)

[^1]: [UML - Architecture](http://www.tutorialspoint.com/uml/uml_architecture.htm)
[^2]: [UML - Modeling Types](http://www.tutorialspoint.com/uml/uml_modeling_types.htm)
[^3]: [UML - Use Case Diagrams](http://www.tutorialspoint.com/uml/uml_use_case_diagram.htm)
[^4]: [Use Case Diagram](https://en.wikipedia.org/wiki/Use_Case_Diagram)
[^5]: [UML Association Between Actor and Use Case](http://www.uml-diagrams.org/use-case-actor-association.html)
[^6]: [Class diagram](https://en.wikipedia.org/wiki/Class_diagram)
[^7]: [Sequence diagram](https://en.wikipedia.org/wiki/Sequence_diagram)
[^8]: [Activity diagram](https://en.wikipedia.org/wiki/Activity_diagram)
[^9]: [Aggregation](http://www.uml-diagrams.org/association.html#aggregation)
[^10]: [UML Class Diagram: Association, Aggregation and Composition](http://aviadezra.blogspot.com/2009/05/uml-association-aggregation-composition.html)
[^11]: [Lecture Notes on Object-Oriented Programming: Object Oriented Aggregation](https://atomicobject.com/resources/oo-programming/object-oriented-aggregation)



