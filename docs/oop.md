# OOP

<blockquote>
  Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which are data structures that contain data, in the form of fields, often known as attributes; and code, in the form of procedures, often known as methods. A distinguishing feature of objects is that an object's procedures can access and often modify the data fields of the object with which they are associated (objects have a notion of "this" or "self"). In OO programming, computer programs are designed by making them out of objects that interact with one another.[1][2] There is significant diversity in object-oriented programming, but most popular languages are class-based, meaning that objects are instances of classes, which typically also determines their type.
</blockquote>

### 1. A First Look


<strong>Procedural vs Object Oriented</strong> [^1]
<img src="http://image.slidesharecdn.com/oop-120229105157-phpapp02/95/object-oriented-concept-13-1024.jpg?cb=1330513070" alt="" />

<strong>Procedural Approach</strong>

<ul>
<li>Focus is on procedures</li>
<li>All data is shared: no protection</li>
<li>More difficult to modify</li>
<li>Hard to manage complexity</li>
</ul>

<strong>Advantages of Object Orientation</strong>

<ul>
<li>People think in terms of object</li>
<li>OO models map to reality </li>
<li>OO models are: Easy to develop &amp; Easy to understand.</li>
</ul>

### 2. Principles

<code>encapsulation</code>, <code>inheritance</code>, <code>abstraction</code>, <code>polymorphism</code> [^2]

![](https://lh3.googleusercontent.com/6dU66WGNNNzUpDIFOjkyMNthwUYtIy5PPU9eo_UpJKUBX7M3u-29=w547-h320-no)
Fundamental Principles of OOP In order for a programming language to be object-oriented, it has to enable working with classes and objects as well as the implementation and use of the fundamental object-oriented principles and concepts: inheritance, abstraction, encapsulation and polymorphism.

<strong>2.1 Encapsulation</strong> [^3] [^4] [^5]

Encapsulation is the packing of data and functions into a single component. The features of encapsulation are supported using classes in most object-oriented programming languages, although other alternatives also exist. It allows selective hiding of properties and methods in an object by building an impenetrable wall to protect the code from accidental corruption.

<small>
<code>What it do?</code> We will learn to hide unnecessary details in our classes and provide a clear and simple interface for working with them.
</small>

<img src="https://datayo.files.wordpress.com/2015/10/b548c-encapsulation-and-abstraction-example-tutorial-download.png" alt="" />

<small>
<code>Example</code>: A popular example you’ll hear for encapsulation is driving a car. Do you need to know exactly how every aspect of a car works (engine, carburettor, alternator, and so on)? No - you need to know how to use the steering wheel, brakes, accelerator, and so on.
</small>

<strong>2.2 Inheritance</strong> [^6] [^7]

Inheritance is when an object or class is based on another object (prototypal inheritance) or class (class-based inheritance), using the same implementation (inheriting from an object or class) specifying implementation to maintain the same behavior (realizing an interface; inheriting behavior).

> **inherit everything, add data or functionality, override functions, super**

<small>
<code>What it do?</code> We will explain how class hierarchies improve code readability and enable the reuse of functionality.
</small>

<img src="https://lh3.googleusercontent.com/eYo9nMAa4e1xSnAawfl7pk3oVpnh0Kz-sPC6oLv49TIipafn7qL_=w934-h501-no" alt="" />

<small>
<code>Example</code>: A real-world example of inheritance is genetic inheritance. We all receive genes from both our parents that then define who we are. We share qualities of both our parents, and yet at the same time are different from them.
</small>

<img src="http://younginc.site11.com/source/5895/images/fig108_01_0.jpg" alt="" />

<small>
<code>Example</code>: we might classify different kinds of vehicles according to the inheritance hierarchy. Moving down the hierarchy, each kind of vehicle is both more specialized than its parent (and all of its ancestors) and more general than its children (and all of its descendants). A wheeled vehicle inherits properties common to all vehicles (it holds one or more people and carries them from place to place) but has an additional property that makes it more specialized (it has wheels). A car inherits properties common to all wheeled vehicles, but has additional, more specialized properties (four wheels, an engine, a body, and so forth). The inheritance relationship can be viewed as an is-a relationship. In this relationship, the objects become more specialized the lower in the hierarchy you go.
</small>

<img src="http://funny-shit.de/wp-content/uploads/2015/01/47036_10150298194574945_476322259_n.jpg" alt="" />

<small>
Look at the image above you will get a point.[^8] Yes, the derived class can access base class properties and still the derived class has its own properties.
</small>

<strong>2.3 Abstraction</strong>

In computer science, abstraction is a technique for managing complexity of computer systems. It works by establishing a level of complexity on which a person interacts with the system, suppressing the more complex details below the current level. The programmer works with an idealized interface (usually well defined) and can add additional levels of functionality that would otherwise be too complex to handle.

<small>
<code>What it do?</code> We will learn how to work through abstractions: to deal with objects considering their important characteristics and ignore all other details.
</small>

<img src="https://lh3.googleusercontent.com/3o597NPwZPNiDUxIR7VP8YrTsPSv3sVHgHM0a-Myc9ceRaehUFrb=w758-h458-no" alt="" />

<small>
<code>Example</code>: You'll never buy a "device", but always buy something more specific : iPhone, Samsung Galaxy, Nokia 3310... Here, iPhone, Samsung Galaxy and Nokia 3310 are concrete things, device is abstract.
</small>

<strong>2.4 Polymorphism</strong> [^9]

Polymorphism is the provision of a single interface to entities of different types. A polymorphic type is one whose operations can also be applied to values of some other type, or types.

<small>
<code>What it do?</code> We will explain how to work in the same manner with different objects, which define a specific implementation of some abstract behavior.
</small>

<img src="http://faculty.orangecoastcollege.edu/sgilbert/lessons/ObjectOrientedConcepts/images/polymorphism.png" alt="" />

<small>
<code>Example</code>: All animal can speak, but dogs woof, cats meow, and ducks quack
</small>

There are two types of polymorphism

<img src="http://i.stack.imgur.com/xmKaT.gif" alt="" />

<ul>
<li>Overloading (compile time polymorphism): methods have the same name but different parameters.</li>
<li>Overriding (run time polymorphism): the implementation given in base class is replaced with that in sub class.</li>
</ul>

<img src="http://i0.wp.com/java9s.com/wp-content/uploads/2012/06/Polymorphism-example.jpg" alt="" />

<small>
<code>Example</code> [^10]: Let us Consider Car example for discussing the polymorphism. Take any brand like Ford, Honda, Toyota, BMW, Benz etc., Everything is  of type Car.
But each have their own advanced features and more advanced technology involved in their move behavior.
</small>

### 3. Concepts

Learn Object Oriented Programming though <a href="https://github.com/justinmeister/Mario-Level-1">Mario Game</a>

[embed]https://www.youtube.com/watch?v=HBbzYKMfx5Y[/embed]

How Mario get `1up`

![](http://gifsec.com/wp-content/uploads/GIF/2014/02/Super-Mario-GIF.gif)

<strong>3.1. Object</strong> [^11]

<blockquote>
  Objects are key to understanding object-oriented technology. Look around right now and you'll find many examples of real-world objects: your dog, your desk, your television set, your bicycle.
</blockquote>

In mario world, <small><img src="http://icons.iconseeker.com/png/32/super-mario/super-paper-mario.png" alt="" />Mario is an object.

<img src="http://findicons.com/files/icons/1274/arcade_daze/32/goomba.png" alt="" /> Goomba is an object. <img src="http://vignette3.wikia.nocookie.net/videogamehistory/images/9/94/Bowser_-_SMB.png/revision/latest?cb=20091229050601" alt="" /> Koopa is also an object. Even a coin<img src="http://icons.iconarchive.com/icons/ph03nyx/super-mario/32/Retro-Coin-icon.png" alt="" /> and a pile <img src="http://noobtuts.com/content/unity/2d-super-mario-bros-game/pipe.png" alt="" /> are objects
</small>

<blockquote>
  Software objects are conceptually similar to real-world objects: they too consist of <strong>state</strong> and related <strong>behavior</strong>.

  An object stores its <strong>state</strong> in <strong>fields</strong> (variables in some programming languages) and exposes its <strong>behavior</strong> through <strong>methods</strong> (functions in some programming languages). Methods operate on an object's internal state and serve as the primary mechanism for object-to-object communication. Hiding internal state and requiring all interaction to be performed through an object's methods is known as data encapsulation — a fundamental principle of object-oriented programming.
</blockquote>

In Mario world, <small>Mario <img src="http://icons.iconseeker.com/png/32/super-mario/super-paper-mario.png" alt="" /> has some fields like position (which indicate where Mario stands), state (which indicate whether Mario alive), and some methods like walk <img src="http://vignette2.wikia.nocookie.net/fantendo/images/2/27/Mario_Walking.gif" alt="" />, fire or jump.
</small>

<small>
Goomba <img src="http://findicons.com/files/icons/1274/arcade_daze/32/goomba.png" alt="" /> has some fields like position (which indicate where Goomba stands), state (which indicate whether Goomba die), and direction (which indicate the direction Goomba moves). Goomba has move method, and jumped_on method (which occurs when it is jumped on by Mario) (Poor Goomba!)
</small>

Mario Objects, real scene
![](https://lh3.googleusercontent.com/qeTVS1oT7XpvDi_PhcKOclFV0wg-JAh2oIoAAYccO7YbAYPwD5Bc=w912-h480-no)

<strong>3.2 Class</strong> [^12]

> In the real world, you'll often find many individual objects all of the same kind. There may be thousands of other bicycles in existence, all of the same make and model. Each bicycle was built from the same set of blueprints and therefore contains the same components. In object-oriented terms, we say that your bicycle is an instance of the class of objects known as bicycles. A class is the blueprint from which individual objects are created.

In Mario world, each coin object come from Coin class, and every Koomba come from Koomba class

![](https://lh3.googleusercontent.com/sTYZvVyQS4inORumcF6IwC9OvEpPJBuh-GnCpwJPi399imm_RngK=w892-h313-no)

**3.3. Inheritance** [^13]

> Inheritance is a mechanism in OOP to design two or more entities that are different but share many common features.

* Feature common to all classes are defined in the `superclass`
* The classes that inherit common features from the `superclass` are called `subclasses`

In Mario World, `Goomba` and `Koopa` is in
![](https://lh3.googleusercontent.com/qUtTgp6NoN8M_0Imh9TPSULleitVDSW7cEHopxB82lxzrsyzENOV=w860-h639-no)

AND MANY, MANY MORE

![](http://img2.wikia.nocookie.net/__cb10/mario-enemies/images/5/50/Wiki-background)

**3.4. Association, Aggregation and Composition**

[^13]

![](http://www.howcsharp.com/img/0/88/difference-between-association-aggregation-and-composition-300x225.jpg)

**Association**:

Whenever two objects are related with each other the relationshiop is called association between object

**Aggregation**:

Aggregation is specialized from of association. In aggregation objects have their own life-cycle but there is ownership and child object can not belongs to another parent object. But this is only an ownership not the life-cycle control of child control through parent object.

Example: Student and Teacher, Person and address

**Composition**

Composition is again specialize form of aggregation and we can call this as `life and death`` relationship. It is a strong type of aggregation. Child object does not have their life-cycle and if parent object is deleted, all child object will also be deleted.

Example: House and room

**3.5 Polymorphism** [^13]

Polymorphism indicates the meaning of "many forms"

Polynorphism present a method that can have many definitions. Polymorphism is related to "over loading" and "over ridding".

Overloading indicates a method can have different definitions by defining different type of parameters.

[code]
getPrice(): void
getPrice(string name): void
[/code]

**3.6 Abstraction** [^13]

Abstraction is the process of modelling only relevant features

- Hide unnecessary details which are irrelevant for current purpose.

Reduces complexity and aids understanding.

Abstraction provides the freedom to defer implementation decisions by avoiding commitments to details.

**3.7 Interface** [^13]

An interface is a contract consisting of group of related function prototypes whose usage is defined but whose implementation is not:

- An interface definition specifies the interface's member functions, called methods, their return types, the number and types of parameters and what they must do.

- These is no implementation associated with an interface.

### 4. Coupling and Cohesion

[^13]

#### 4.1 Coupling

Coupling defines how dependent one object on another object (that is uses).

Coupling is a measure of strength of connection between any two system components. The more any one components knows about other components, the tighter (worse) the coupling is between those components.

#### 4.2 Cohesion

Cohesion defines how narrowly defined an object is. Functional cohesion refers measures how strongly objects are related.

Cohesion is a measure of how logically related the parts of an individual components are to each other, and to the overall components. The more logically related the parts of components are to each other higher (better) the cohesion of that components.

#### 4.3 Object Oriented Design

Low coupling and tight cohesion is good object oriented design.

<h3>Challenge</h3>

<h4>Object</h4>

<strong>Task 1</strong>: With boiler plate code, make an gif image (32x32) Mario fire ball and jump to get coins

### 5. NEXT

* Design Principles
* Design Patterns

[^1]: <a href="http://www.slideshare.net/smj/object-oriented-concept">Object Oriented Concept slideshare</a>
[^2]: <a href="http://www.introprogramming.info/english-intro-csharp-book/read-online/chapter-20-object-oriented-programming-principles/#_Toc362296565">Chapter 20. Object-Oriented Programming Principles (OOP)</a>
[^3]: <a href="http://csdoop.blogspot.com/2015/03/object-oriented-programming.html">Object Oriented Programming</a>
[^4]: <a href="http://gamedevelopment.tutsplus.com/tutorials/quick-tip-the-oop-principle-of-encapsulation--gamedev-2187">Quick Tip: The OOP Principle of Encapsulation</a>
[^5]: <a href="https://en.wikipedia.org/wiki/Encapsulation_(computer_programming)">Encapsulation (computer programming)</a>
[^6]: <a href="https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming)">Inheritance (object-oriented programming)</a>
[^7]: <a href="http://gamedevelopment.tutsplus.com/tutorials/quick-tip-the-oop-principle-of-inheritance--gamedev-2536">Quick Tip: The OOP Principle of Inheritance</a>
[^8]: <a href="https://www.quora.com/What-are-the-practical-real-life-examples-of-polymorphism-inheritance-composition-overriding-encapsulation-abstraction-and-other-important-concepts-of-OOPS">What are the practical (real life) examples of polymorphism, inheritance, composition, overriding, encapsulation, abstraction and other important concepts of OOPS?</a>
[^9]: <a href="https://en.wikipedia.org/wiki/Polymorphism_(computer_science)">Polymorphism (computer science)</a>
[^10]: <a href="http://java9s.com/core-java/polymorphism-in-java">Polymorphism in Java</a>
[^11]: <a href="https://docs.oracle.com/javase/tutorial/java/concepts/object.html">What Is an Object?</a>
[^12]: <a href="https://docs.oracle.com/javase/tutorial/java/concepts/class.html">What Is a Class?</a>
[^13]: <a href="http://www.slideshare.net/sangharshcs/advance-oops-concepts-8752156">Advance oops concepts</a>