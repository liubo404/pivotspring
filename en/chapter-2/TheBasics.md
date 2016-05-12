## The Basics
Any application system is make of components that work together to solve a problem. In object-oriented design they are called _classes_. Figure2-1 depicts the sequence of operations necessary to create a Person instance. Bacause this chapter is about Spring Core, a web application is not needed, so request to manipulate Person instances will be directed to implementations of the PersonManager interface. Implementations of this interface will provide access to the database using an implementation of PersonRepository interface. The operatin is pretty simple and the setup to write and execute the code should be too. This is where Spring comes in--providing a way to build an application using **p**lan **o**ld **J**ava **o**bject(POJOs)[^1] and applying enterprise services(transaction execution, remote execution) noninvasively.

[^1]A software term introduced by Martin Fowler, Rebeca Parsons, and Josh MacKenzie in September 2000 to refer to ordinary Java objects not bound by any restriction.

![Figure 2-1](../../../img/f21.png)

_**Figure2-1**. UML sequence of operations necessary to create a Person instance_

The components making up an application interact and depend on one another. Defining how those objects are composed is quite difficult using plain Java. Even with the help of all the design patterns defined by experts in the software industry, the work is still cumbersome, as the pattern components still have to be implemented before used. The Spring _invertion of control_(IoC) container was degined to help developers compose objects into fully working applications, ready to use[^2].

