---
title: Zaznanie sytuacji, w których należy użyć C# przesłonięć i nowych słów kluczowych — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 0a209b9522202649765654013fdc3a468913c6b1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714782"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)

W C#programie Metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie bazowej. Możesz określić sposób działania metod przy użyciu słów kluczowych [New](../../language-reference/keywords/new-modifier.md) i [override](../../language-reference/keywords/override.md) . Modyfikator `override` *rozszerza* metodę klasy bazowej `virtual`, a modyfikator `new` *ukrywa* dostępną metodę klasy bazowej. Różnica przedstawiono w przykładach w tym temacie.  
  
 W aplikacji konsoli Zadeklaruj poniższe dwie klasy `BaseClass` i `DerivedClass`. `DerivedClass` dziedziczy z `BaseClass`.  
  
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
  
 W metodzie `Main` Zadeklaruj zmienne `bc`, `dc`i `bcdc`.  
  
- `bc` jest typu `BaseClass`, a jego wartość jest typu `BaseClass`.  
  
- `dc` jest typu `DerivedClass`, a jego wartość jest typu `DerivedClass`.  
  
- `bcdc` jest typu `BaseClass`, a jego wartość jest typu `DerivedClass`. Jest to zmienna, do której należy zwrócić uwagę.  
  
 Ponieważ `bc` i `bcdc` mają `BaseClass`typu, mogą bezpośrednio uzyskać dostęp do `Method1`, chyba że używasz rzutowania. Zmienna `dc` ma dostęp do `Method1` i `Method2`. Te relacje są pokazane w poniższym kodzie.  
  
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
  
 Następnie Dodaj następującą metodę `Method2`, aby `BaseClass`. Podpis tej metody pasuje do sygnatury metody `Method2` w `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Ponieważ `BaseClass` teraz ma metodę `Method2`, druga instrukcja wywołująca może zostać dodana dla zmiennych `BaseClass` `bc` i `bcdc`, jak pokazano w poniższym kodzie.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Podczas kompilowania projektu, zobaczysz, że dodanie metody `Method2` w `BaseClass` powoduje ostrzeżenie. Ostrzeżenie informuje, że metoda `Method2` w `DerivedClass` ukrywa metodę `Method2` w `BaseClass`. Zaleca się użycie słowa kluczowego `new` w definicji `Method2`, jeśli zamierzasz mieć ten wynik. Alternatywnie można zmienić nazwę jednej z `Method2` metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktycznie możliwe.  
  
 Przed dodaniem `new`Uruchom program, aby zobaczyć dane wyjściowe generowane przez dodatkowe instrukcje wywoływania. Zostaną wyświetlone następujące wyniki.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Słowo kluczowe `new` zachowuje relacje, które tworzą dane wyjściowe, ale pomija ostrzeżenie. Zmienne, które mają typ `BaseClass` nadal mają dostęp do elementów członkowskich `BaseClass`, a zmienna, która ma typ `DerivedClass` nadal uzyskuje dostęp do elementów członkowskich w `DerivedClass`, a następnie do rozważania członków dziedziczonych z `BaseClass`.  
  
 Aby pominąć ostrzeżenie, Dodaj modyfikator `new` do definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie. Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Ponownie uruchom program, aby sprawdzić, czy dane wyjściowe nie uległy zmianie. Sprawdź również, czy ostrzeżenie nie jest już wyświetlane. Korzystając z `new`, potwierdzasz, że użytkownik, który modyfikuje, ukrywa element członkowski, który jest Dziedziczony z klasy bazowej. Aby uzyskać więcej informacji na temat ukrywania nazw poprzez dziedziczenie, zobacz [New modyfikator](../../language-reference/keywords/new-modifier.md).  
  
 Aby w przeciwieństwie do efektów używania `override`, należy dodać następującą metodę do `DerivedClass`. Modyfikator `override` można dodać przed `public`lub po nim.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Dodaj modyfikator `virtual` do definicji `Method1` w `BaseClass`. Modyfikator `virtual` można dodać przed `public`lub po nim.  
  
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
  
 Użycie modyfikatora `override` umożliwia `bcdc` dostępu do metody `Method1` zdefiniowanej w `DerivedClass`. Zwykle jest to wymagane zachowanie w hierarchiach dziedziczenia. Obiekty mające wartości, które są tworzone na podstawie klasy pochodnej, są używane do używania metod, które są zdefiniowane w klasie pochodnej. W tym celu należy użyć `override`, aby zwiększyć metodę klasy bazowej.  
  
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
  
 Poniższy przykład ilustruje podobne zachowanie w innym kontekście. W przykładzie zdefiniowano trzy klasy: Klasa bazowa o nazwie `Car` i dwie klasy, które pochodzą od niej, `ConvertibleCar` i `Minivan`. Klasa bazowa zawiera metodę `DescribeCar`. Metoda wyświetla podstawowy opis samochodu, a następnie wywołuje `ShowDetails`, aby uzyskać dodatkowe informacje. Każda z tych trzech klas definiuje metodę `ShowDetails`. Modyfikator `new` służy do definiowania `ShowDetails` w klasie `ConvertibleCar`. Modyfikator `override` służy do definiowania `ShowDetails` w klasie `Minivan`.  
  
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
  
 Przykład sprawdza, która wersja `ShowDetails` jest wywoływana. Poniższa metoda, `TestCars1`, deklaruje wystąpienie każdej klasy, a następnie wywołuje `DescribeCar` dla każdego wystąpienia.  
  
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
  
 `TestCars1` generuje następujące dane wyjściowe. Zwróć uwagę na szczególnie wyniki `car2`, które prawdopodobnie nie są oczekiwane. Typ obiektu jest `ConvertibleCar`, ale `DescribeCar` nie uzyskuje dostępu do wersji `ShowDetails` zdefiniowanej w klasie `ConvertibleCar`, ponieważ ta metoda jest zadeklarowana z modyfikatorem `new`, a nie modyfikatorem `override`. W związku z tym obiekt `ConvertibleCar` wyświetla ten sam opis, co obiekt `Car`. Należy odróżniać wyniki `car3`, który jest obiektem `Minivan`. W takim przypadku Metoda `ShowDetails` zadeklarowana w klasie `Minivan` przesłania metodę `ShowDetails`, która jest zadeklarowana w klasie `Car`, a opis wyświetlany opisuje minivan.  
  
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
  
 `TestCars2` tworzy listę obiektów, które mają `Car`typu. Wartości obiektów są tworzone na podstawie klas `Car`, `ConvertibleCar`i `Minivan`. `DescribeCar` jest wywoływana dla każdego elementu listy. Poniższy kod przedstawia definicję `TestCars2`.  
  
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
  
 Wyświetlane są następujące dane wyjściowe. Zwróć uwagę, że jest to taka sama jak wartość wyjściowa wyświetlana przez `TestCars1`. Metoda `ShowDetails` klasy `ConvertibleCar` nie jest wywoływana, niezależnie od tego, czy typ obiektu jest `ConvertibleCar`, jak w `TestCars1`, czy `Car`, jak w `TestCars2`. Z kolei `car3` wywołuje metodę `ShowDetails` z klasy `Minivan` w obu przypadkach, niezależnie od tego, czy ma `Minivan` typu, czy typu `Car`.  
  
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
  
 Metody `TestCars3` i `TestCars4` wykonania przykładu. Te metody wywołują `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowanych do typu `ConvertibleCar` i `Minivan` (`TestCars3`), a następnie z obiektów zadeklarowanych do typu `Car` (`TestCars4`). Poniższy kod definiuje te dwie metody.  
  
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
- [abstract](../../language-reference/keywords/abstract.md)
