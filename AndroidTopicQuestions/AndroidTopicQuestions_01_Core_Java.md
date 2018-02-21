# Android Interview Topic Review

Please review the questions below in each section, research the answers on our CodePath guides and any other sources (StackOverflow, official docs) and then write up a complete answer (between a few sentences and a few paragraphs) for each of the questions below.

## 1. Core Java
Research and answer the following core Java questions:

1.
> What is the difference between abstract classes and interfaces?

Abstract classes require subclasses to extend from the Abstract class to inherit behavior. It contains both concrete and abstract methods. Abstract classes cannot be instantiated.

Interfaces are a blueprint/contract of a class and require classes to implement an interface's methods to represent the common behavior. The subclasses provide the implementation to the methods.

2.
> Describe the value of an interface and why are they important?


Interfaces allow a class to represent many roles and behaviors. Due to java's limitation of single inheritance, interfaces provide an alternative for a class to represent different abstractions. This characteristic provides flexibility to allow a class already inheriting a class or requiring multiple roles to achieve the needed abstraction.

3.
>What are anonymous classes?

Anonymous classes are an inner class without a name and only a single object is created. They are useful in writing implementation classes for listener interfaces.

4.
>What is the difference between using == and .equals on a string?

The "==" syntax compares if the String object is the same instance while the ".equals" method compares the values of two strings.

5.
>What is composition and what is inheritance in object-oriented programming? Why would you use one over another?

Composition is when a object is composed of other objects or has references to other objects. Inheritance is when a object inherits or "extends" another object's behavior/methods. Composition would be used when you want a class to have additional logic and behavior but are unable to extend another class due to Java's single inheritance limitation. Composition would also be used when you want to encapsulate or hide this behavior. Inheritance would be used when you want a child class to be treated as the inherited class and only add/extend exposed additional behavior.

6.
>What is polymorphism and give an example where this is useful?

Polymorphism is the concept of having an object that can represent many things i.e. roles, behavior. This is useful when you want to treat/control a group of objects through a common abstraction/interface but having the client class unaware of the implementation details. An example is the ViewGroup interface in Android, where common behaviors and logic that apply to all types of ViewGroups (addView(), getChildCount()) is exposed in the interface, but the implementation is hidden in the concrete implementations i.e. LinearLayout, RelativeLayout etc.

7.
>When would you make an object value final? When you want to make an variable static?

You would make an object final if you did not want the instance or value of the object to change. You would want to make the object static if you wanted the object to keep it's same value during the lifetime of the application.

8.
>What is the difference between between method overloading and overriding?

Method overloadding is when you have the same method name but have different method arguments/signature. Method overriding is when you modify an inherited or interface method providing additional or different logic implementation.

9.
>What is serialization in Java (not Android)? How do you implement it? How about in Android?

Serialization in Java is the concept of taking a class and converting it to a format (sequence of bytes) for transport or storage (i.e. across a network) so it can be recreated later keeping the original state and data. You implement it by having a class implement the Serializable interface. Serialization is implemented in Android the same way, but using Serializable is not recommended as its performance (due to Reflection and additional object creation overhead,
also causing more garbage collection to occur) is poorer. Android would use Parcelable in order to achieve similar behavior.

10.
>Do objects get passed by reference or value in Java? Elaborate on that.

Java objects get passed by value. To elaborate, Java manipulates objects "by reference" but it passes objects references to methods "by value". For example, in a swap method you would be passing copies of the references not the original ones as method arguments.

11.
>What are generics and why are they important in Java?

Generics is a system in Java to provide templates. The idea is to allow a type to be a parameter to methods, classes and interfaces. They are important since it provides a mechanism for compile-time type checking and can help avoid errors when type-casting. It allows a type or method to operate on objects of various types.

12.
> What is one design pattern that you use and find helpful in Java/Android?

I find the "Builder" design pattern useful in Java/Android. The "Builder" pattern eases the construction of objects and provides a mechanism to exclude optional parameters, and avoid long multiple argument constructors which leads to less error prone code.
