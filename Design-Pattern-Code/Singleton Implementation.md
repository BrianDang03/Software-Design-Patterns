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
