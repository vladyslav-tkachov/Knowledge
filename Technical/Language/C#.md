## **1. Basics: Variables, Data Types, and Input/Output**

### **Code Example: Hello World, Variables, and Input**
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        // Print a greeting
        Console.WriteLine("Hello, C#!");

        // Declare variables
        string name = "Alice";
        int age = 25;
        double height = 5.6;

        // Input from the user
        Console.Write("Enter your name: ");
        string userName = Console.ReadLine();
        Console.WriteLine($"Hello, {userName}! Welcome to C#!");
    }
}
```

### **Key Concepts**
- **Variables**: `int`, `double`, `string`, `bool`, etc.
- **Input**: `Console.ReadLine()` reads user input as a string.
- **Output**: `Console.WriteLine()` and `Console.Write()`.

---

## **2. Conditional Statements**

### **Code Example: If/Else**
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.Write("Enter your score: ");
        int score = int.Parse(Console.ReadLine());

        if (score >= 90)
        {
            Console.WriteLine("Grade: A");
        }
        else if (score >= 75)
        {
            Console.WriteLine("Grade: B");
        }
        else if (score >= 60)
        {
            Console.WriteLine("Grade: C");
        }
        else
        {
            Console.WriteLine("Grade: F");
        }
    }
}
```

### **Key Concepts**
- Conditions use operators like `==`, `!=`, `<`, `>`, `<=`, `>=`.
- `int.Parse()` converts input to an integer.

---

## **3. Loops**

### **Code Example: For and While**
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        // For loop
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Count: {i}");
        }

        // While loop
        int counter = 5;
        while (counter > 0)
        {
            Console.WriteLine($"Countdown: {counter}");
            counter--;
        }
    }
}
```

### **Key Concepts**
- `for (initialization; condition; increment)` is great for definite loops.
- `while (condition)` is ideal for indefinite loops.

---

## **4. Functions**

### **Code Example: Functions and Return Values**
```csharp
using System;

class Program
{
    static int Factorial(int n)
    {
        if (n == 0 || n == 1)
            return 1;
        return n * Factorial(n - 1);
    }

    static void Main(string[] args)
    {
        Console.WriteLine($"Factorial of 5 is {Factorial(5)}");
    }
}
```

### **Key Concepts**
- Functions are defined using `returnType functionName(parameters)`.
- Recursive functions call themselves to solve smaller subproblems.

---

## **5. Lists and Dictionaries**

### **Code Example: Lists**
```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main(string[] args)
    {
        List<string> fruits = new List<string> { "Apple", "Banana", "Cherry" };
        fruits.Add("Orange");
        Console.WriteLine(fruits[1]);  // Access by index
        Console.WriteLine(fruits.Count);  // Length of the list
    }
}
```

### **Code Example: Dictionaries**
```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main(string[] args)
    {
        Dictionary<string, int> ages = new Dictionary<string, int>
        {
            { "Alice", 25 },
            { "Bob", 30 }
        };

        Console.WriteLine(ages["Alice"]);
        ages["Bob"] = 31;  // Update a value
        Console.WriteLine(ages["Bob"]);
    }
}
```

### **Key Concepts**
- **Lists**: Dynamic collections of items.
- **Dictionaries**: Key-value pairs for efficient lookups.

---

## **6. Classes and OOP**

### **Code Example: Object-Oriented Programming**
```csharp
using System;

class Dog
{
    public string Name { get; set; }
    public int Age { get; set; }

    public Dog(string name, int age)
    {
        Name = name;
        Age = age;
    }

    public string Bark()
    {
        return $"{Name} says Woof!";
    }
}

class Program
{
    static void Main(string[] args)
    {
        Dog myDog = new Dog("Buddy", 3);
        Console.WriteLine(myDog.Bark());
    }
}
```

### **Key Concepts**
- Classes encapsulate data and behavior.
- Properties like `Name` use `get` and `set`.
- Objects are instances of classes.

---

## **7. File Handling**

### **Code Example: Read/Write Files**
```csharp
using System;
using System.IO;

class Program
{
    static void Main(string[] args)
    {
        // Write to a file
        File.WriteAllText("example.txt", "Hello, file handling!");

        // Read from a file
        string content = File.ReadAllText("example.txt");
        Console.WriteLine(content);
    }
}
```

### **Key Concepts**
- Use `File.WriteAllText()` and `File.ReadAllText()` for simple file I/O.
- Use `StreamWriter` or `StreamReader` for more control.

---

## **8. Error Handling**

### **Code Example: Try/Except**
```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        try
        {
            Console.Write("Enter a number: ");
            int number = int.Parse(Console.ReadLine());
            Console.WriteLine($"Square: {number * number}");
        }
        catch (FormatException)
        {
            Console.WriteLine("That's not a valid number!");
        }
    }
}
```

### **Key Concepts**
- Use `try`, `catch`, and optionally `finally` to handle errors.

---

## **9. Using LINQ (Advanced Querying)**

### **Code Example: LINQ on Lists**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main(string[] args)
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6 };
        var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();

        Console.WriteLine(string.Join(", ", evenNumbers));  // Output: 2, 4, 6
    }
}
```

### **Key Concepts**
- LINQ (Language-Integrated Query) is used for querying collections like lists.

---

## **10. Advanced Topics**

### **Delegates**
```csharp
using System;

class Program
{
    delegate int Operation(int x, int y);

    static int Add(int x, int y) => x + y;
    static int Multiply(int x, int y) => x * y;

    static void Main(string[] args)
    {
        Operation op = Add;
        Console.WriteLine(op(3, 4));  // Output: 7

        op = Multiply;
        Console.WriteLine(op(3, 4));  // Output: 12
    }
}
```

### **Async/Await**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        await Task.Delay(1000);
        Console.WriteLine("Hello, async world!");
    }
}
```

---

## **11. Generics**

### **Code Example: Generic Classes and Methods**
```csharp
using System;
using System.Collections.Generic;

class GenericBox<T>
{
    public T Value { get; set; }

    public GenericBox(T value)
    {
        Value = value;
    }

    public void Display()
    {
        Console.WriteLine($"Value: {Value}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        GenericBox<int> intBox = new GenericBox<int>(123);
        GenericBox<string> stringBox = new GenericBox<string>("Hello");

        intBox.Display(); // Output: Value: 123
        stringBox.Display(); // Output: Value: Hello
    }
}
```

### **Key Concepts**
- Generics provide type safety while maintaining flexibility.
- Avoids redundant code by allowing methods/classes to work with any data type.

---

## **12. Events and Delegates**

### **Code Example: Custom Event Handling**
```csharp
using System;

class Alarm
{
    public delegate void AlarmTriggeredEventHandler();
    public event AlarmTriggeredEventHandler AlarmTriggered;

    public void Trigger()
    {
        Console.WriteLine("Alarm Triggered!");
        AlarmTriggered?.Invoke();
    }
}

class Program
{
    static void Main(string[] args)
    {
        Alarm alarm = new Alarm();
        alarm.AlarmTriggered += () => Console.WriteLine("Take action!");

        alarm.Trigger(); // Output: Alarm Triggered! Take action!
    }
}
```

### **Key Concepts**
- **Delegates**: Type-safe pointers to methods.
- **Events**: Encapsulation of delegate invocation, ensuring controlled usage.

---

## **13. Extension Methods**

### **Code Example: Adding New Methods**
```csharp
using System;

static class StringExtensions
{
    public static string Reverse(this string str)
    {
        char[] charArray = str.ToCharArray();
        Array.Reverse(charArray);
        return new string(charArray);
    }
}

class Program
{
    static void Main(string[] args)
    {
        string message = "Hello, World!";
        Console.WriteLine(message.Reverse()); // Output: !dlroW ,olleH
    }
}
```

### **Key Concepts**
- Adds methods to existing classes without modifying their source code.
- Must be in a static class and marked with the `this` keyword.

---

## **14. Reflection**

### **Code Example: Inspecting Metadata**
```csharp
using System;
using System.Reflection;

class Program
{
    static void Main(string[] args)
    {
        Type type = typeof(string);
        Console.WriteLine($"Type: {type.FullName}");

        MethodInfo[] methods = type.GetMethods();
        foreach (var method in methods)
        {
            Console.WriteLine(method.Name);
        }
    }
}
```

### **Key Concepts**
- Reflection enables runtime type inspection.
- Use cases include plugins, dependency injection, and serialization.

---

## **15. Threading**

### **Code Example: Multi-threading**
```csharp
using System;
using System.Threading;

class Program
{
    static void PrintNumbers()
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"Number: {i}");
            Thread.Sleep(500); // Simulate work
        }
    }

    static void Main(string[] args)
    {
        Thread thread = new Thread(PrintNumbers);
        thread.Start();
        Console.WriteLine("Main thread continues...");
    }
}
```

### **Key Concepts**
- `Thread` enables concurrent execution of code.
- Use `Thread.Sleep` for delays.

---

## **16. Task Parallel Library (TPL)**

### **Code Example: Parallel Programming**
```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        Task task1 = Task.Run(() => Console.WriteLine("Task 1"));
        Task task2 = Task.Run(() => Console.WriteLine("Task 2"));

        await Task.WhenAll(task1, task2);
    }
}
```

### **Key Concepts**
- TPL provides better thread management than manual threading.
- Use `Task` for scalable parallel programming.

---

## **17. LINQ: Advanced Operations**

### **Code Example: Grouping and Sorting**
```csharp
using System;
using System.Collections.Generic;
using System.Linq;

class Program
{
    static void Main(string[] args)
    {
        List<string> fruits = new List<string> { "Apple", "Banana", "Cherry", "Apple" };

        var groupedFruits = fruits.GroupBy(f => f).OrderBy(g => g.Key);

        foreach (var group in groupedFruits)
        {
            Console.WriteLine($"{group.Key}: {group.Count()}");
        }
    }
}
```

### **Key Concepts**
- LINQ supports grouping, sorting, and aggregation over collections.
- Common LINQ methods: `GroupBy`, `OrderBy`, `SelectMany`.

---

## **18. Dependency Injection**

### **Code Example: Constructor Injection**
```csharp
using System;

interface ILogger
{
    void Log(string message);
}

class ConsoleLogger : ILogger
{
    public void Log(string message) => Console.WriteLine(message);
}

class Application
{
    private readonly ILogger _logger;

    public Application(ILogger logger)
    {
        _logger = logger;
    }

    public void Run() => _logger.Log("Application is running.");
}

class Program
{
    static void Main(string[] args)
    {
        ILogger logger = new ConsoleLogger();
        Application app = new Application(logger);
        app.Run(); // Output: Application is running.
    }
}
```

### **Key Concepts**
- Separates object creation from business logic.
- Improves testability and maintainability.

---

## **19. Design Patterns**

### **Code Example: Singleton**
```csharp
using System;

class Singleton
{
    private static Singleton _instance;

    private Singleton() { }

    public static Singleton Instance => _instance ??= new Singleton();
}

class Program
{
    static void Main(string[] args)
    {
        Singleton s1 = Singleton.Instance;
        Singleton s2 = Singleton.Instance;
        Console.WriteLine(s1 == s2); // Output: True
    }
}
```

### **Key Concepts**
- Singleton ensures a class has only one instance.
- Common design patterns: Factory, Observer, Strategy.

---

## **20. Unit Testing**

### **Code Example: Using NUnit**
```csharp
using NUnit.Framework;

[TestFixture]
public class CalculatorTests
{
    [Test]
    public void Add_AddsTwoNumbers_ReturnsSum()
    {
        int result = Calculator.Add(2, 3);
        Assert.AreEqual(5, result);
    }
}

public static class Calculator
{
    public static int Add(int x, int y) => x + y;
}
```

### **Key Concepts**
- Use frameworks like NUnit, MSTest, or xUnit.
- Write tests to ensure reliability.

---

## **21. Asynchronous Programming**

### **Code Example: Async/Await with File I/O**
```csharp
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        string content = "Hello, async file handling!";
        await File.WriteAllTextAsync("example.txt", content);

        string result = await File.ReadAllTextAsync("example.txt");
        Console.WriteLine(result);
    }
}
```

### **Key Concepts**
- Asynchronous programming improves application responsiveness.

---

## **22. C# Best Practices**
1. **Use `var` wisely**: For readability, avoid overuse.
2. **Error handling**: Always handle exceptions with `try/catch`.
3. **Naming conventions**: Use PascalCase for methods/classes and camelCase for variables.
4. **Immutable types**: Use `readonly` and `const` where applicable.
5. **Avoid magic numbers**: Use named constants.

---

### **Resources**
1. [C# Documentation (Microsoft)](https://learn.microsoft.com/en-us/dotnet/csharp/)
2. [C# Programming Guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/)
3. [NUnit Documentation](https://nunit.org/)

