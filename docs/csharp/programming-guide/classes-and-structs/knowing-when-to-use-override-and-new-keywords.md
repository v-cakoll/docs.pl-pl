---
title: Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 61bfa87b7aaa7c17d4ba67c69fa1e57ee7415dc0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
W języku C# metody w klasie pochodnej może mieć taką samą nazwę jak metody w klasie podstawowej. Można określić sposób interakcji metody przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) i [zastąpienia](../../../csharp/language-reference/keywords/override.md) słów kluczowych. `override` Modyfikator *rozszerza* metody klasy podstawowej i `new` modyfikator *ukrywa* go. Różnice przedstawiono w przykładach w niniejszym temacie.  
  
 W aplikacji konsoli, należy zadeklarować następujące dwie klasy `BaseClass` i `DerivedClass`. `DerivedClass` dziedziczy `BaseClass`.  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 W `Main` metody, Zadeklaruj zmienne `bc`, `dc`, i `bcdc`.  
  
-   `bc` Typ jest `BaseClass`, a jego wartość jest typu `BaseClass`.  
  
-   `dc` Typ jest `DerivedClass`, a jego wartość jest typu `DerivedClass`.  
  
-   `bcdc` Typ jest `BaseClass`, a jego wartość jest typu `DerivedClass`. Jest to zmienna, aby zwrócić uwagę na.  
  
 Ponieważ `bc` i `bcdc` ma typ `BaseClass`, tylko bezpośrednio uzyskać dostęp do `Method1`, chyba że używasz rzutowania. Zmienna `dc` dostęp zarówno do `Method1` i `Method2`. Te relacje są wyświetlane w poniższym kodzie.  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 Następnie dodaj następujące `Method2` metodę `BaseClass`. Podpis tej metody pasuje do podpisu `Method2` metoda `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Ponieważ `BaseClass` ma teraz `Method2` metody, druga instrukcja wywoływania można dodać do `BaseClass` zmienne `bc` i `bcdc`, jak pokazano w poniższym kodzie.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Podczas kompilowania projektu widać, że dodanie `Method2` metoda `BaseClass` powoduje, że ostrzeżenie. Komunikat ostrzeżenia, że `Method2` metody w `DerivedClass` ukrywa `Method2` metoda `BaseClass`. Zaleca się używania `new` — słowo kluczowe w `Method2` definicji, jeśli zamierzasz spowodować tego wyniku. Alternatywnie można zmienić nazwę jednej z `Method2` metody umożliwiające rozwiązanie to ostrzeżenie, ale nie jest zawsze praktyczne.  
  
 Przed dodaniem `new`, uruchom program, aby zobaczyć dane wyjściowe, generowane przez dodatkowe instrukcje wywołującego. Następujące wyniki są wyświetlane.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` — Słowo kluczowe chroni relacje, które wywołują te dane wyjściowe, ale jego pominięcie ostrzeżenia. Zmienne, które mają typ `BaseClass` dostęp do elementów członkowskich w dalszym ciągu `BaseClass`i zmienna, która ma typ `DerivedClass` w dalszym ciągu dostęp do elementów członkowskich w `DerivedClass` pierwszy, a następnie należy wziąć pod uwagę członków dziedziczonych po elemencie `BaseClass`.  
  
 Aby pominąć to ostrzeżenie, Dodaj `new` modyfikator do definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie. Modyfikator mogą być dodawane przed lub po `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie uległy zmianie. Sprawdź także, czy ostrzeżenia nie będzie już wyświetlany. Za pomocą `new`, są potwierdzające, że masz świadomość, że element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczona z klasy podstawowej. Aby uzyskać więcej informacji o nazwie ukrywanie poprzez dziedziczenie, zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Natomiast takie zachowanie skutki za pomocą do `override`, dodaj następującą metodę do `DerivedClass`. `override` Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Dodaj `virtual` modyfikator do definicji `Method1` w `BaseClass`. `virtual` Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Uruchom ponownie projekt. Zwróć uwagę szczególnie ostatnie dwa wiersze następujące dane wyjściowe.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Korzystanie z `override` umożliwia modyfikator `bcdc` dostępu `Method1` metodę, która jest zdefiniowana w `DerivedClass`. Zazwyczaj jest to zachowanie w hierarchii dziedziczenia. Chcesz obiektów, które mają wartości, które są tworzone na podstawie klasy pochodnej w celu użycia metody, które są zdefiniowane w klasie pochodnej. To zachowanie można osiągnąć za pomocą `override` rozszerzenie metody klasy podstawowej.  
  
 Poniższy kod zawiera pełny przykład.  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 Poniższy przykład przedstawia podobne zachowanie w kontekście innej. W przykładzie zdefiniowano trzech klas: klasa podstawowa o nazwie `Car` i dwie klasy, które są pochodnymi, `ConvertibleCar` i `Minivan`. Klasa podstawowa zawiera `DescribeCar` metody. Metoda zawiera opis podstawowych samochodu, a następnie wywołuje `ShowDetails` o podanie dodatkowych informacji. Definiuje trzy klas `ShowDetails` metody. `new` Modyfikator służy do definiowania `ShowDetails` w `ConvertibleCar` klasy. `override` Modyfikator służy do definiowania `ShowDetails` w `Minivan` klasy.  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 Przykład sprawdza wersję `ShowDetails` jest wywoływana. Następujące metody `TestCars1`, deklaruje wystąpienia każdej klasy, a następnie wywołuje `DescribeCar` na każde wystąpienie.  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 `TestCars1` tworzy następujące dane wyjściowe. Zwróć uwagę, szczególnie wyniki dla `car2`, które są prawdopodobnie niż oczekiwano. Typ obiektu jest `ConvertibleCar`, ale `DescribeCar` nie dostępu do wersji `ShowDetails` zdefiniowanego w `ConvertibleCar` klasy, ponieważ ta metoda jest zadeklarowany za pomocą `new` modyfikator, nie `override` modyfikator. W związku z tym `ConvertibleCar` obiekt wyświetla ten sam opis co `Car` obiektu. Natomiast wyników dla `car3`, która jest `Minivan` obiektu. W takim przypadku `ShowDetails` metodę, która jest zadeklarowana w `Minivan` klasy zastąpienia `ShowDetails` metodę, która jest zadeklarowana w `Car` klasy i opis, który jest wyświetlany w tym artykule opisano Mały furgon.  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 `TestCars2` Tworzy listę obiektów, które mają typ `Car`. Wartości te obiekty są utworzone z `Car`, `ConvertibleCar`, i `Minivan` klasy. `DescribeCar` jest wywoływana dla każdego elementu listy. Poniższy kod przedstawia definicję `TestCars2`.  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 Następujące dane wyjściowe są wyświetlane. Zwróć uwagę, że jest taka sama jak dane wyjściowe, który jest wyświetlany za `TestCars1`. `ShowDetails` Metody `ConvertibleCar` klasy nie zostanie wywołany, niezależnie od tego, czy typ obiektu `ConvertibleCar`, jak w `TestCars1`, lub `Car`, jak w `TestCars2`. Z drugiej strony `car3` wywołania `ShowDetails` metody z `Minivan` klasy w obu przypadkach, czy ma typ `Minivan` lub typ `Car`.  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 Metody `TestCars3` i `TestCars4` ukończyć przykład. Te metody mogą wywoływać `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowany typ `ConvertibleCar` i `Minivan` (`TestCars3`), następnie z obiektów zadeklarowany typ `Car` (`TestCars4`). Poniższy kod definiuje te dwie metody.  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 Te metody powodują następujące dane wyjściowe, co odpowiada wyników z pierwszego przykładu, w tym temacie.  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 Poniższy kod przedstawia kompletnego projektu i jego dane wyjściowe.  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [base](../../../csharp/language-reference/keywords/base.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)
