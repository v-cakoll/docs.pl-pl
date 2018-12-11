---
title: Użycie przesłonięć i nowych słów kluczowych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: d44d8d0143d366117a24495df3fa8a18f893ebb3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244742"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)
W języku C# metody w klasie pochodnej może mieć taką samą nazwę jak metody w klasie bazowej. Można określić sposób interakcji metody przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) i [zastąpienia](../../../csharp/language-reference/keywords/override.md) słów kluczowych. `override` Modyfikator *rozszerza* metody klasy bazowej i `new` modyfikator *ukrywa* go. Różnica jest przedstawionych w przykładach w tym temacie.  
  
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
  
 W `Main` metody deklarować zmienne `bc`, `dc`, i `bcdc`.  
  
-   `bc` Typ jest `BaseClass`, a jej wartość jest typu `BaseClass`.  
  
-   `dc` Typ jest `DerivedClass`, a jej wartość jest typu `DerivedClass`.  
  
-   `bcdc` Typ jest `BaseClass`, a jej wartość jest typu `DerivedClass`. Jest to zmienna, na które należy zwrócić uwagę.  
  
 Ponieważ `bc` i `bcdc` typ `BaseClass`, tylko bezpośrednio uzyskać dostęp do `Method1`, chyba że używasz rzutowania. Zmienna `dc` dostęp zarówno do `Method1` i `Method2`. Te relacje są wyświetlane w poniższym kodzie.  
  
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
  
 Następnie dodaj następujące `Method2` metody `BaseClass`. Podpis tej metody pasuje do podpisu `Method2` method in Class metoda `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Ponieważ `BaseClass` ma teraz `Method2` metody, druga instrukcja wywołującego można dodać `BaseClass` zmienne `bc` i `bcdc`, jak pokazano w poniższym kodzie.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Podczas tworzenia projektu, zobaczysz, że dodanie `Method2` method in Class metoda `BaseClass` powoduje, że ostrzeżenie. To ostrzeżenie jest wyświetlany komunikat, który `Method2` method in Class metoda `DerivedClass` ukrywa `Method2` method in Class metoda `BaseClass`. Zaleca się używać `new` — słowo kluczowe w `Method2` definicji, jeśli zamierzasz spowodować, że wynik. Alternatywnie, można zmienić nazwę jednej z `Method2` metody umożliwiające rozwiązanie to ostrzeżenie, ale nie jest zawsze możliwe.  
  
 Przed dodaniem `new`, uruchom program, aby wyświetlić dane wyjściowe generowane przez dodatkowe instrukcje wywoływania. Są wyświetlane następujące wyniki.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 `new` — Słowo kluczowe chroni relacje, które tworzą te dane wyjściowe, ale jej umożliwia pominięcie ostrzeżenia. Zmienne, które mają typ `BaseClass` w dalszym ciągu uzyskać dostęp do składowych aspektów `BaseClass`i zmienna, która ma typ `DerivedClass` w dalszym ciągu dostęp do elementów członkowskich w `DerivedClass` pierwszy, a następnie należy wziąć pod uwagę członków dziedziczonych po elemencie `BaseClass`.  
  
 Aby pominąć to ostrzeżenie, należy dodać `new` modyfikatora definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie. Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie zmienił się. Sprawdź także, że ostrzeżenie nie jest już wyświetlany. Za pomocą `new`, są potwierdzające, że masz świadomość, element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczony z klasy bazowej. Aby uzyskać więcej informacji na temat ukrywanie nazw poprzez dziedziczenie, zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).  
  
 Natomiast takie zachowanie do efektów do `override`, dodaj następującą metodę do `DerivedClass`. `override` Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Dodaj `virtual` modyfikatora definicji `Method1` w `BaseClass`. `virtual` Modyfikator można dodać przed lub po `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Uruchom projekt ponownie. Zwróć uwagę, szczególnie ostatnie dwa wiersze następujące dane wyjściowe.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 Korzystanie z `override` modyfikator umożliwia `bcdc` dostęp do `Method1` metodę, która jest zdefiniowana w `DerivedClass`. Zazwyczaj jest to żądane zachowanie w hierarchii dziedziczenia. Chcesz, aby obiekty, które mają wartości, które są tworzone na podstawie klasy pochodnej w celu użycia metod, które są zdefiniowane w klasie pochodnej. To zachowanie można osiągnąć za pomocą `override` rozszerzenie metody klasy bazowej.  
  
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
  
 Poniższy przykład ilustruje podobne zachowanie w innym kontekście. W przykładzie zdefiniowano trzech klas: klasa bazowa o nazwie `Car` i dwie klasy, które są uzyskiwane z nich, `ConvertibleCar` i `Minivan`. Klasa bazowa zawiera `DescribeCar` metody. Metoda zawiera podstawowy opis metodyki samochód, a następnie wywołuje `ShowDetails` dostarczenie dodatkowych informacji. Każdy z trzech klas definiuje `ShowDetails` metody. `new` Modyfikator jest używany do definiowania `ShowDetails` w `ConvertibleCar` klasy. `override` Modyfikator jest używany do definiowania `ShowDetails` w `Minivan` klasy.  
  
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
  
 Przykład sprawdza wersję `ShowDetails` jest wywoływana. Następującą metodę `TestCars1`, deklaruje wystąpienia każdej klasy, a następnie wywołuje `DescribeCar` w każdym wystąpieniu.  
  
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
  
 `TestCars1` generuje następujące wyniki. Zwróć uwagę, szczególnie wyniki `car2`, które są prawdopodobnie niż oczekiwano. Typ obiektu jest `ConvertibleCar`, ale `DescribeCar` nie uzyskać dostępu do wersji `ShowDetails` zdefiniowanego w `ConvertibleCar` klasy, ponieważ ta metoda jest zadeklarowana za pomocą `new` modyfikator, nie `override` modyfikator. W rezultacie `ConvertibleCar` obiekt wyświetla ten sam opis co `Car` obiektu. Porównaj wyniki `car3`, czyli `Minivan` obiektu. W tym przypadku `ShowDetails` metodę, która jest zadeklarowana w `Minivan` klasy zastąpienia `ShowDetails` metodę, która jest zadeklarowana w `Car` klasy i opis, który jest wyświetlany w tym artykule opisano Mały furgon.  
  
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
  
 `TestCars2` Tworzy listę obiektów, które mają typ `Car`. Wartości, które obiekty są tworzone z `Car`, `ConvertibleCar`, i `Minivan` klasy. `DescribeCar` jest wywoływana dla każdego elementu listy. Poniższy kod przedstawia definicję `TestCars2`.  
  
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
  
 Następujące dane wyjściowe są wyświetlane. Zauważ, że jest taki sam jak wynik wyświetlony po `TestCars1`. `ShowDetails` Metody `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, czy typ obiektu `ConvertibleCar`, jak w `TestCars1`, lub `Car`, jak w `TestCars2`. Z drugiej strony `car3` wywołania `ShowDetails` metody z `Minivan` klasy w obu przypadkach, czy zawiera on typ `Minivan` lub typ `Car`.  
  
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
  
 Metody `TestCars3` i `TestCars4` kompletny przykład. Wywoływanie tych metod `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowany typ `ConvertibleCar` i `Minivan` (`TestCars3`), następnie z obiektami niezadeklarowanymi typ `Car` (`TestCars4`). Poniższy kod definiuje te dwie metody.  
  
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
  
 Metody generuje następujące dane wyjściowe, co odpowiada wyników z pierwszego przykładu w tym temacie.  
  
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
  
 Poniższy kod przedstawia kompletny projektu i jego danych wyjściowych.  
  
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

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Przechowywanie wersji przesłonięć i nowych słów kluczowych](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
- [base](../../../csharp/language-reference/keywords/base.md)  
- [abstract](../../../csharp/language-reference/keywords/abstract.md)
