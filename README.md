# Software-Design-Patterns

<details>
  <summary>Singleton</summary>
  
  - Definition
    - A software design pattern that restricts the instantiation of a class to a singular instance.
  - Uses Cases
    -  Logging is a common real-world use case for singletons, because all objects that wish to log messages require a uniform point of access and conceptually write to a single source.
- Pros
  - The pattern is useful when exactly one object is needed to coordinate actions across a system.
  - Allows classes to ensure only one instance, have easy access to the instance, and control instantiation like hiding a constructor.
- Cons
- How to Implement
    - Implementations of the singleton pattern ensure that only one instance of the singleton class ever exists and typically provide global access to that instance.
    - Declaring all constructors of the class to be private, which prevents it from being instantiated by other objects
    - Providing a static method that returns a reference to the instance
    - The instance is usually stored as a private static variable; the instance is created when the variable is initialized, at some point before when the static method is first called.
    - [Singleton Implementation](Design-Pattern-Code/SingletonImplementation.md)

    
- Work Cited
  1. https://en.wikipedia.org/wiki/Singleton_pattern  
</details>
