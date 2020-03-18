---
title: Wiedząc, kiedy używać zastępowania i nowych słów kluczowych - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 493c6c5f5bf47c6b2cd140ac0f6922f91ca4252b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170263"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)

W języku C#metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie podstawowej. Można określić, jak metody współdziałają przy użyciu [nowych](../../language-reference/keywords/new-modifier.md) i [zastąpić](../../language-reference/keywords/override.md) słowa kluczowe. Modyfikator `override` *rozszerza* metodę `virtual` klasy podstawowej, a `new` modyfikator *ukrywa* metodę dostępnej klasy podstawowej. Różnica jest zilustrowana w przykładach w tym temacie.  
  
 W aplikacji konsoli zadeklarować następujące `BaseClass` dwie `DerivedClass`klasy i . `DerivedClass`dziedziczy `BaseClass`z .  
  
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
  
 W `Main` metodzie deklaruj `bc`zmienne , `dc`i `bcdc`.  
  
- `bc`jest typu, `BaseClass`a jego wartość `BaseClass`jest typu .  
  
- `dc`jest typu, `DerivedClass`a jego wartość `DerivedClass`jest typu .  
  
- `bcdc`jest typu, `BaseClass`a jego wartość `DerivedClass`jest typu . Jest to zmienna, na jaką należy zwrócić uwagę.  
  
 Ponieważ `bc` `bcdc` i `BaseClass`mają typ , `Method1`mogą uzyskać bezpośredni dostęp , chyba że używasz odlewania. Zmienna `dc` może `Method1` `Method2`uzyskać dostęp do obu i . Te relacje są wyświetlane w poniższym kodzie.  
  
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
  
 Następnie dodaj `Method2` następującą `BaseClass`metodę do . Podpis tej metody jest zgodny `Method2` z `DerivedClass`podpisem metody w pliku .  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Ponieważ `BaseClass` teraz `Method2` ma metodę, można dodać drugą `BaseClass` instrukcję wywołującą dla zmiennych `bc` i `bcdc`, jak pokazano w poniższym kodzie.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Podczas tworzenia projektu, widać, że dodanie `Method2` metody `BaseClass` powoduje ostrzeżenie. Ostrzeżenie mówi, `Method2` że `DerivedClass` metoda w `Method2` ukrywa `BaseClass`metodę w . Zaleca się użycie `new` słowa kluczowego w `Method2` definicji, jeśli zamierzasz spowodować ten wynik. Alternatywnie można zmienić nazwę jednej `Method2` z metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktyczne.  
  
 Przed `new`dodaniem uruchom program, aby wyświetlić dane wyjściowe wytwarzane przez dodatkowe instrukcje wywołujące. Zostaną wyświetlone następujące wyniki.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Słowo `new` kluczowe zachowuje relacje, które produkują, że dane wyjściowe, ale pomija ostrzeżenie. Zmienne, które mają `BaseClass` typ, nadal `BaseClass`uzyskują dostęp do `DerivedClass` elementów członkowskich , `DerivedClass` a zmienna, która ma `BaseClass`typ, nadal uzyskuje dostęp do elementów członkowskich w pierwszej kolejności, a następnie do rozważenia członków dziedziczonych z .  
  
 Aby pominąć ostrzeżenie, `new` dodaj modyfikator do definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie. Modyfikator można dodać `public`przed lub po .  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie uległy zmianie. Sprawdź również, czy ostrzeżenie nie jest już wyświetlane. Za `new`pomocą , potwierdzasz, że są świadomi, że element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczony z klasy podstawowej. Aby uzyskać więcej informacji na temat ukrywania nazw w dziedziczeniu, zobacz [nowy modyfikator](../../language-reference/keywords/new-modifier.md).  
  
 Aby porównać to zachowanie z `override`efektami używania, `DerivedClass`dodaj następującą metodę do . Modyfikator `override` można dodać `public`przed lub po .  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Dodaj `virtual` modyfikator do `Method1` `BaseClass`definicji w . Modyfikator `virtual` można dodać `public`przed lub po .  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Uruchom ponownie projekt. Zwróć uwagę zwłaszcza na ostatnie dwa wiersze następujących danych wyjściowych.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Użycie `override` modyfikatora `bcdc` umożliwia `Method1` dostęp do metody `DerivedClass`zdefiniowanej w programie . Zazwyczaj jest to pożądane zachowanie w hierarchiach dziedziczenia. Chcesz, aby obiekty, które mają wartości, które są tworzone z klasy pochodnej, aby użyć metod, które są zdefiniowane w klasie pochodnej. Można osiągnąć to `override` zachowanie przy użyciu rozszerzenia metody klasy podstawowej.  
  
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
  
 Poniższy przykład ilustruje podobne zachowanie w innym kontekście. W przykładzie zdefiniowano trzy klasy: klasę podstawową o `Car` nazwie `ConvertibleCar` `Minivan`i dwie klasy, które pochodzą z niego i . Klasa podstawowa `DescribeCar` zawiera metodę. Metoda wyświetla podstawowy opis samochodu, a `ShowDetails` następnie wywołuje dodatkowe informacje. Każda z trzech klas `ShowDetails` definiuje metodę. Modyfikator `new` służy `ShowDetails` do `ConvertibleCar` definiowania w klasie. Modyfikator `override` służy `ShowDetails` do `Minivan` definiowania w klasie.  
  
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
  
 Przykład testuje, `ShowDetails` która wersja jest wywoływana. Następująca metoda `TestCars1`, deklaruje wystąpienie każdej klasy, `DescribeCar` a następnie wywołuje każde wystąpienie.  
  
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
  
 `TestCars1`wytwarza następujące dane wyjściowe. Zwróć uwagę `car2`zwłaszcza na wyniki dla , które prawdopodobnie nie są to, czego się spodziewałeś. Typ `ConvertibleCar`obiektu jest , `DescribeCar` ale nie ma `ShowDetails` dostępu do wersji, `ConvertibleCar` która jest zdefiniowana `new` w klasie, `override` ponieważ ta metoda jest zadeklarowana za pomocą modyfikatora, a nie modyfikatora. W rezultacie `ConvertibleCar` obiekt wyświetla ten sam `Car` opis jako obiekt. Kontrast wyniki `car3`dla , `Minivan` który jest obiektem. W takim przypadku `ShowDetails` metoda, która `Minivan` jest zadeklarowana `ShowDetails` w klasie zastępuje `Car` metodę, która jest zadeklarowana w klasie, a opis, który jest wyświetlany opisuje minivan.  
  
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
  
 `TestCars2`tworzy listę obiektów, które `Car`mają typ . Wartości obiektów są tworzone z `Car`, `ConvertibleCar`i `Minivan` klas. `DescribeCar`jest wywoływana na każdym elemencie listy. Poniższy kod przedstawia definicję . `TestCars2`  
  
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
  
 Zostanie wyświetlone następujące dane wyjściowe. Należy zauważyć, że jest taka sama jak `TestCars1`dane wyjściowe, które są wyświetlane przez . Metoda `ShowDetails` `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, `ConvertibleCar`czy typ `TestCars1`obiektu `Car`jest `TestCars2`, jak w , lub , jak w . I `car3` odwrotnie `ShowDetails` wywołuje metodę `Minivan` z klasy w obu `Minivan` przypadkach, `Car`czy ma typ lub typ .  
  
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
  
 Metody `TestCars3` i `TestCars4` wypełnić przykład. Te metody `ShowDetails` wywołać bezpośrednio, najpierw z `ConvertibleCar` `Minivan` obiektów`TestCars3`zadeklarowanych jako typ `Car` i`TestCars4`( ), a następnie z obiektów zadeklarowanych jako typu ( ). Poniższy kod definiuje te dwie metody.  
  
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
  
 Metody dają następujące dane wyjściowe, co odpowiada wynikom z pierwszego przykładu w tym temacie.  
  
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
  
 Poniższy kod przedstawia cały projekt i jego dane wyjściowe.  
  
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

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](./index.md)
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [Abstrakcja](../../language-reference/keywords/abstract.md)
