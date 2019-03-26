# DesignPatternsInJava

# Creational Patterns:

  - 1. Factory Method Pattern:
    - Allows the sub-classes to choose the type of objects to create
    - loose-coupling by eliminating the need to bind application-specific classes into the code
    
    - Usage:
      - when a class doesn't know what sub-classes will be required to create
      - sub-classes specify the objects to be created
      - parent classes choose the creation of objects to its sub-classes
      
    - Example:
      - GenerateBill -> GetPlanFactory -> Plan ( abstract class )------- 1. DomesticPlan
                                                                      -- 2. CommercialPlan
                                                                      -- 3. InstitutionalPlan
                                                                      
  - 2. Abstract Factory Pattern:
    - AbstractFacotry lets a class returns a factory of classes. Then the corresponding Factory class can be used to 
      get the final implementation of the child class
    - It eases the exchanging of object families
    - Promotes consistency among objects
    
    - Usage:
      - when system needs to be independent of how its objects are created, composed and represented
      - Family of related objects has to be used together, then this constraint is enforced
      - provie a library of objects that doesn't show implementations and only reveals interfaces
      - system needs to be configured with one of a multiple family objects
      
    - Example:
    
      - ClientCode -> FactoryCreator -> AbstractFactory ( abstract class ) ----- 1. Bank Factory
                                                                                        - (creates) Bank
                                                                                        ----- 1. HDFC
                                                                                        ----- 2. ICICI
                                                                                        ----- 3. SBI
                                                                           ----- 2. Loan Factory
                                                                                        - (creates) Loan
                                                                                        ----- 1. HomeLoan
                                                                                        ----- 2. BusinessLoan
                                                                                        ----- 3. EducationLoan
  - 3. Singleton Pattern:
    - A class that has only one instance and provides a global point of access to it
      - Early Initialization
      - Lazy Initialization
      
    - Example:
    
      - Singleton ::-instance ::getInstance(): Singleton
      
  - 4. Prototype Pattern:
    - Cloning of an existing object instead of creating new one and can also be customized as per the requirement
    
    - Advantages:
      - Reduces the need of sub-classing
      - hides complexities of creating objects
      - clients can get new objects without knowing which type of object it will be
      - lets you add/remove objects at runtime
      
    - ProtypeDemo -> EmployeeRecord <----- Prototype ( getClone():Prototype )
    
  - 5. Builder Pattern:
    - Construct a complex object from simple object using step-by-step approach.
    
    - Advantages:
      - Provides clear separation between the construction and representation of an object
      - better control over construction process
      - supports to change the internal representatin of objects
      
    - Example:
    
      - BuilderDemo -> CDBuilder {buildSonyCd():CDType, buildSamsungCd:CDType) -> CDType { pack, price } -> CD <--- Packing
                                                                                                            -------> Company ( Abstract class )
                                                                                                                      --------> Sony
                                                                                                                      --------> Samsung
                                                                                                                      
  - 6. Object Pool Pattern:
    - To reuse objects that are expensive to create
    - Objects in the pool have a lifecycle: creation, validation and destory
    
    - Advantages:
      - Most effective in a situation where the rate of initializing a class instance is high
      
    - Example:
    
      - ObjectPoolDemo -> ExportingTask -> ExportingProcess
                                        -> ObjectPool
                                            { borrowObject(),
                                              returnObject(),
                                              shutdownPool(),
                                              createObject(),
                                              initialize(..) }
                                              
    - Uses a java ConcurrentLinkedQueue data structure to store and retrieve the objects
    - Also uses a threadpool executor to fill the objects when the size of the pool is less than the desired size
    
# Structural Patterns:

  - 1. Adapter Pattern:
      - Converts the interface of a class into anothor interface that a client wants
      - Wrapper class
      
      - Used when:
        - object needs to utilize an existing class with an incompatible interface
        - create reusable class that cooperates with classes which don't have compatible interfaces
      
      - Example:
      
        - AdapterPatternDemo -> CreditCard ( target interface ) <----- BankCustomer -----> BankDetails
        
  - 2. Bridge Pattern:
      - Decouple the functional abstraction from the implementation so that the two can vary independently
      
      - Example:
      
        - BridgePatternDemo -> QuestionFormat <---extends-- QuestionManager (bridge class) -> Question (interface) <----- JavaQuestions
  
  - 3. Composite Pattern:
      - allow clients to operate in generic manner on objects that may or may not represent a hierarchy of objects
      
      - Advantages:
        - Define class heirarchies that contain primitive and complex objects
        - makes easier to add new kind of components
        
      - Used when:
        - represent a full or partial hierarchy of objects
        - when the responsibilities are needed to be added dynamically to the individual objects without affecting other objects.
        
      - Example:
      
        - Client -> Component
                        -----------> Composite
                        -----------> Leaf

        - CompositePatternDemo -> Employee
                                      ----------- Accoutant
                                      ----------- Cashier
                                      ----------- BankManager
                                      
  - 4. Decorator Pattern:
      - Attaches a flexible additional responsibilities to an object dynamically
      - Also known as Wrapper
      
      - Advantages:
        - Provides greater flexibility than static inheritance
        - enhances extensibility of objects
        
      - DecoratorPatternCustomer -> Food 
                                      ---------> VegFood
                                      ---------> FoodDecorator
                                                    -----------> NonVegFood
                                                    -----------> ChineeseFood
  - 5. Facade Pattern:
      - just provide a unified and simplified interface to a set of interfaces in a subsystem, therefore it hides the complexities of 
        the subsystem from the client
        
      - Example:
      
        - FacadePatternClient -> ShopKeeper -> MobileShop (interface)
                                                      -------> IPhone
                                                      -------> Samsung
                                                      -------> Blackberry
                                                      
    - 6. Flyweight pattern:    
        - to reuse already existing similar kind of objects by storing them and create new object when no matching object is found
        
        
    - 7. Proxy Pattern:
        - provides the control for accessing the original object
        - its also called Surrogate or Placeholder.
        
        - Used:
          - VirtualProxy
          - ProtectiveProxy
          - RemoteProxy
          - SmartProxy
          
        - Example:
            ProxyPatternClient -> OfficeInternetAccess (interface)
                                            -------------> ProxyInternetAccess
                                            -------------> RealinternetAccess
  
  
  
  
