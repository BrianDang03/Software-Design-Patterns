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
<details>
  <summary>Code</summary>

  <details>
    <summary>singleton.cpp</summary>
  
  ```cpp    
  #include "singleton.hpp"

  // Get the Singleton Instance
  Singleton& Singleton::Get()
  {
      if (nullptr == instance)
      {
          instance = new Singleton();
      }
  
      return *instance;
  }
  
  // Destory the Singleton Instance
  void Singleton::Destruct()
  {
      delete instance;
      instance = nullptr;
  }
  
  // Private Constructor
  Singleton::Singleton() : value(0) { /* Other Intilization Code */ }
  
  // Private Destructor
  Singleton::~Singleton() { /* Cleanup code */ }
  
  // Initalize the Instance
  Singleton *Singleton::instance = nullptr;
  ```

  </details>

  <details>
    <summary>singleton.hpp</summary>
  
  ```cpp    
  #ifndef SINGLETON_HPP
  #define SINGLETON_HPP
  
  class Singleton
  {
    public:
        // Static method to get the singleton instance
        static Singleton& Get();
  
        // Rule of Three
        // Prevents copying of Singleton instance
        Singleton(const Singleton&) = delete;
  
        // Prevents Assignment from one Singelton instance to another
        Singleton& operator=(const Singleton&) = delete;
  
        // Destorys the Singleton instance and frees memory
        static void Destruct();
  
        // Interface Methods for value
        int GetValue() { return value; }
        void SetValue(int aValue) { value = aValue; }
  
    private:
        // No public Constructor
        Singleton();
  
        // No public Destructor
        ~Singleton();
  
        // Declaration Class Variable
        static Singleton* instance;
        // Data
        int value;
  };
  
  #endif
  ```

  </details>
  
  <details>
    <summary>main.cpp</summary>
  
  ```cpp    
  #include <iostream>
  #include "singleton.hpp"
  
  int main()
  {
      Singleton& singleton = Singleton::Get();
      
      std::cout << "Value = " << singleton.GetValue() << "\n";
      
      singleton.SetValue(42);
      std::cout << "Value = " << singleton.GetValue() << "\n";
  
      Singleton::Destruct();
      
      return 0;
  }
  ```

  </details>
</details>
    
- Work Cited
  1. https://en.wikipedia.org/wiki/Singleton_pattern  
</details>
