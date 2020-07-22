---
title: Zaznanie sytuacji, w których należy użyć przesłonięć i nowych słów kluczowych — Przewodnik programowania w języku C#
description: Użyj słowa kluczowego new i override w języku C#, aby określić, jak metody o tej samej nazwie w klasie podstawowej i pochodnej współdziałają z nimi.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864543"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)

W języku C# Metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie bazowej. Możesz określić sposób działania metod przy użyciu słów kluczowych [New](../../language-reference/keywords/new-modifier.md) i [override](../../language-reference/keywords/override.md) . `override`Modyfikator *rozszerza* metodę klasy bazowej `virtual` , a `new` modyfikator *ukrywa* dostępną metodę klasy bazowej. Różnica przedstawiono w przykładach w tym temacie.  
  
 W aplikacji konsoli Zadeklaruj poniższe dwie klasy `BaseClass` i `DerivedClass` . `DerivedClass`dziedziczy z `BaseClass` .  
  
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
  
 W `Main` metodzie Zadeklaruj zmienne `bc` , `dc` , i `bcdc` .  
  
- `bc`jest typu `BaseClass` , a jego wartość jest typu `BaseClass` .  
  
- `dc`jest typu `DerivedClass` , a jego wartość jest typu `DerivedClass` .  
  
- `bcdc`jest typu `BaseClass` , a jego wartość jest typu `DerivedClass` . Jest to zmienna, do której należy zwrócić uwagę.  
  
 Ze względu na to, że `bc` i `bcdc` mają typ `BaseClass` , mogą oni jedynie bezpośrednio uzyskać dostęp `Method1` , chyba że używasz rzutowania. Zmienna `dc` ma dostęp do obu `Method1` i `Method2` . Te relacje są pokazane w poniższym kodzie.  
  
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
  
 Następnie Dodaj następującą `Method2` metodę do `BaseClass` . Podpis tej metody jest zgodny z podpisem `Method2` metody w `DerivedClass` .  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Ponieważ `BaseClass` ma teraz `Method2` metodę, można dodać drugą instrukcję wywołującą dla `BaseClass` zmiennych `bc` i `bcdc` , jak pokazano w poniższym kodzie.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Podczas kompilowania projektu, zobaczysz, że dodanie `Method2` metody w `BaseClass` powoduje ostrzeżenie. Ostrzeżenie oznacza, że `Method2` Metoda w programie `DerivedClass` ukrywa `Method2` metodę w `BaseClass` . Zaleca się użycie `new` słowa kluczowego w `Method2` definicji, jeśli zamierzasz mieć ten wynik. Alternatywnie można zmienić nazwę jednej z `Method2` metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktycznie możliwe.  
  
 Przed dodaniem `new` programu Uruchom program, aby zobaczyć dane wyjściowe generowane przez dodatkowe instrukcje wywoływania. Zostaną wyświetlone następujące wyniki.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new`Słowo kluczowe zachowuje relacje, które tworzą dane wyjściowe, ale pomija ostrzeżenie. Zmienne, które mają typ `BaseClass` , nadal uzyskują dostęp do elementów członkowskich `BaseClass` , a zmienna, która ma typ, `DerivedClass` nadal uzyskuje dostęp do członków w `DerivedClass` pierwszej kolejności, a następnie do rozważania członków dziedziczonych z `BaseClass` .  
  
 Aby pominąć ostrzeżenie, Dodaj `new` modyfikator do definicji `Method2` w `DerivedClass` , jak pokazano w poniższym kodzie. Modyfikator można dodać przed lub po `public` .  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Ponownie uruchom program, aby sprawdzić, czy dane wyjściowe nie uległy zmianie. Sprawdź również, czy ostrzeżenie nie jest już wyświetlane. Przy użyciu `new` , potwierdzasz, że użytkownik ma świadomość, że modyfikowany członek ukrywa element członkowski, który jest Dziedziczony z klasy bazowej. Aby uzyskać więcej informacji na temat ukrywania nazw poprzez dziedziczenie, zobacz [New modyfikator](../../language-reference/keywords/new-modifier.md).  
  
 Aby w przeciwieństwie do efektów używania, należy `override` dodać następującą metodę do `DerivedClass` . `override`Modyfikator można dodać przed lub po `public` .  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Dodaj `virtual` modyfikator do definicji elementu `Method1` w `BaseClass` . `virtual`Modyfikator można dodać przed lub po `public` .  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Uruchom ponownie projekt. Zwróć uwagę na szczególnie ostatnie dwa wiersze następujących danych wyjściowych.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Użycie `override` modyfikatora umożliwia dostęp do `bcdc` `Method1` metody, która jest zdefiniowana w `DerivedClass` . Zwykle jest to wymagane zachowanie w hierarchiach dziedziczenia. Obiekty mające wartości, które są tworzone na podstawie klasy pochodnej, są używane do używania metod, które są zdefiniowane w klasie pochodnej. To zachowanie można osiągnąć za pomocą polecenia, `override` Aby zwiększyć metodę klasy bazowej.  
  
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
  
 Poniższy przykład ilustruje podobne zachowanie w innym kontekście. W przykładzie zdefiniowano trzy klasy: Klasa bazowa o nazwie `Car` i dwie klasy, które są od niej pochodne `ConvertibleCar` i `Minivan` . Klasa bazowa zawiera `DescribeCar` metodę. Metoda wyświetla podstawowy opis samochodu, a następnie wywołuje `ShowDetails` w celu podania dodatkowych informacji. Każda z tych trzech klas definiuje `ShowDetails` metodę. `new`Modyfikator służy do definiowania `ShowDetails` w `ConvertibleCar` klasie. `override`Modyfikator służy do definiowania `ShowDetails` w `Minivan` klasie.  
  
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
  
 Przykład sprawdza, która wersja programu `ShowDetails` jest wywoływana. Poniższa metoda, `TestCars1` deklaruje wystąpienie każdej klasy, a następnie wywołuje `DescribeCar` każde wystąpienie.  
  
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
  
 `TestCars1`tworzy następujące dane wyjściowe. Zwróć uwagę na szczególnie wyniki dla `car2` , które prawdopodobnie nie są oczekiwane. Typ obiektu to `ConvertibleCar` , ale nie `DescribeCar` uzyskuje dostępu do wersji `ShowDetails` , która jest zdefiniowana w `ConvertibleCar` klasie, ponieważ ta metoda jest zadeklarowana z `new` modyfikatorem, a nie `override` modyfikatorem. W efekcie `ConvertibleCar` obiekt wyświetla ten sam opis, co `Car` obiekt. Umożliwia odróżnienie wyników dla `car3` , które jest `Minivan` obiektem. W tym przypadku metoda, `ShowDetails` która jest zadeklarowana w `Minivan` klasie przesłania `ShowDetails` metodę zadeklarowaną w `Car` klasie, a wyświetlany opis opisuje minivan.  
  
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
  
 `TestCars2`tworzy listę obiektów, które mają typ `Car` . Wartości obiektów są tworzone na podstawie `Car` `ConvertibleCar` klas,, i `Minivan` . `DescribeCar`jest wywoływana dla każdego elementu listy. Poniższy kod przedstawia definicję `TestCars2` .  
  
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
  
 Wyświetlane są następujące dane wyjściowe. Zwróć uwagę, że jest to taka sama jak wartość wyjściowa wyświetlana przez `TestCars1` . `ShowDetails`Metoda `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, czy typ obiektu to `ConvertibleCar` , jak w `TestCars1` , lub `Car` , jak w `TestCars2` . Odwrotnie, `car3` wywołuje `ShowDetails` metodę z `Minivan` klasy w obu przypadkach, niezależnie od tego, czy ma typ `Minivan` lub typ `Car` .  
  
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
  
 Metody `TestCars3` i `TestCars4` Dokończ przykład. Metody te są wywoływane `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowanych jako typu `ConvertibleCar` i `Minivan` ( `TestCars3` ), a następnie z obiektów zadeklarowanych jako typu `Car` ( `TestCars4` ). Poniższy kod definiuje te dwie metody.  
  
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
  
 Metody te generują następujące dane wyjściowe, które odpowiadają wynikom z pierwszego przykładu w tym temacie.  
  
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
  
 Poniższy kod przedstawia kompletny projekt i jego dane wyjściowe.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](./index.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [streszczeń](../../language-reference/keywords/abstract.md)
