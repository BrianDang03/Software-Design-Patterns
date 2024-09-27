# Software-Design-Patterns

<details>
  <summary>Singleton</summary>
  
- Definition
  - A software design pattern that restricts the instantiation of a class to a singular instance.
- Uses Cases
  -  Logging is a common real-world use case for singletons, because all objects that wish to log messages require a uniform point of access and conceptually write to a single source.
  -  Configuration Manager where it becomes a single place to access application-wide settings.
  -  Database Connection Pool is a singular manager that corrdinates database connections.
- Pros
  - The pattern is useful when exactly one object is needed to coordinate actions across a system.
  - Allows class to ensure only one instance, have easy global access to the instance, and control instantiation like hiding a constructor.
  - Saves memory and resources due to only having one instance of the class.
  - The Singleton class is only created when it is needed thus reducing resource usage.
- Cons
  -  Due to the global point access nature of the Singleton class, other classes can become too dependent on the Singleton thus making the system harder to refactor and scale.
  -  Violates the Single Responsibility Principle (SRP) becasue the Singleton controls both the instance creation and its functions/behaviors.
  -  If a different class and function changes the state of the Singleton, other classes that rely on the Singleton may change.
  -  Future design decisions will be effect due to the private constructor. This makes the Singleton impossible to inherit and polymorth from thus harder to scale and adapt to different contexts of the code base.
- How to Implement
  - Implementations of the singleton pattern ensure that only one instance of the singleton class ever exists and typically provide global access to that instance.
  - Declaring all constructors of the class to be private, which prevents it from being instantiated by other objects
  - Providing a static method that returns a reference to the instance
  - The instance is usually stored as a private static variable; the instance is created when the variable is initialized, at some point before when the static method is first called
  - [Code](https://github.com/BrianDang03/Software-Design-Patterns/blob/main/Design-Pattern-Code/SingletonCode.md)
- Work Cited
  1. https://en.wikipedia.org/wiki/Singleton_pattern
  2. ChatGPT
 
</details>
