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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="510c4-103">Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="510c4-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="510c4-104">W języku C# Metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="510c4-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="510c4-105">Możesz określić sposób działania metod przy użyciu słów kluczowych [New](../../language-reference/keywords/new-modifier.md) i [override](../../language-reference/keywords/override.md) .</span><span class="sxs-lookup"><span data-stu-id="510c4-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="510c4-106">`override`Modyfikator *rozszerza* metodę klasy bazowej `virtual` , a `new` modyfikator *ukrywa* dostępną metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="510c4-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="510c4-107">Różnica przedstawiono w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="510c4-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="510c4-108">W aplikacji konsoli Zadeklaruj poniższe dwie klasy `BaseClass` i `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="510c4-109">`DerivedClass`dziedziczy z `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="510c4-110">W `Main` metodzie Zadeklaruj zmienne `bc` , `dc` , i `bcdc` .</span><span class="sxs-lookup"><span data-stu-id="510c4-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="510c4-111">`bc`jest typu `BaseClass` , a jego wartość jest typu `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="510c4-112">`dc`jest typu `DerivedClass` , a jego wartość jest typu `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="510c4-113">`bcdc`jest typu `BaseClass` , a jego wartość jest typu `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="510c4-114">Jest to zmienna, do której należy zwrócić uwagę.</span><span class="sxs-lookup"><span data-stu-id="510c4-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="510c4-115">Ze względu na to, że `bc` i `bcdc` mają typ `BaseClass` , mogą oni jedynie bezpośrednio uzyskać dostęp `Method1` , chyba że używasz rzutowania.</span><span class="sxs-lookup"><span data-stu-id="510c4-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="510c4-116">Zmienna `dc` ma dostęp do obu `Method1` i `Method2` .</span><span class="sxs-lookup"><span data-stu-id="510c4-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="510c4-117">Te relacje są pokazane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="510c4-117">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="510c4-118">Następnie Dodaj następującą `Method2` metodę do `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="510c4-119">Podpis tej metody jest zgodny z podpisem `Method2` metody w `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="510c4-120">Ponieważ `BaseClass` ma teraz `Method2` metodę, można dodać drugą instrukcję wywołującą dla `BaseClass` zmiennych `bc` i `bcdc` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="510c4-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="510c4-121">Podczas kompilowania projektu, zobaczysz, że dodanie `Method2` metody w `BaseClass` powoduje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="510c4-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="510c4-122">Ostrzeżenie oznacza, że `Method2` Metoda w programie `DerivedClass` ukrywa `Method2` metodę w `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="510c4-123">Zaleca się użycie `new` słowa kluczowego w `Method2` definicji, jeśli zamierzasz mieć ten wynik.</span><span class="sxs-lookup"><span data-stu-id="510c4-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="510c4-124">Alternatywnie można zmienić nazwę jednej z `Method2` metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktycznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="510c4-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="510c4-125">Przed dodaniem `new` programu Uruchom program, aby zobaczyć dane wyjściowe generowane przez dodatkowe instrukcje wywoływania.</span><span class="sxs-lookup"><span data-stu-id="510c4-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="510c4-126">Zostaną wyświetlone następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="510c4-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="510c4-127">`new`Słowo kluczowe zachowuje relacje, które tworzą dane wyjściowe, ale pomija ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="510c4-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="510c4-128">Zmienne, które mają typ `BaseClass` , nadal uzyskują dostęp do elementów członkowskich `BaseClass` , a zmienna, która ma typ, `DerivedClass` nadal uzyskuje dostęp do członków w `DerivedClass` pierwszej kolejności, a następnie do rozważania członków dziedziczonych z `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="510c4-129">Aby pominąć ostrzeżenie, Dodaj `new` modyfikator do definicji `Method2` w `DerivedClass` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="510c4-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="510c4-130">Modyfikator można dodać przed lub po `public` .</span><span class="sxs-lookup"><span data-stu-id="510c4-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="510c4-131">Ponownie uruchom program, aby sprawdzić, czy dane wyjściowe nie uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="510c4-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="510c4-132">Sprawdź również, czy ostrzeżenie nie jest już wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="510c4-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="510c4-133">Przy użyciu `new` , potwierdzasz, że użytkownik ma świadomość, że modyfikowany członek ukrywa element członkowski, który jest Dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="510c4-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="510c4-134">Aby uzyskać więcej informacji na temat ukrywania nazw poprzez dziedziczenie, zobacz [New modyfikator](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="510c4-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="510c4-135">Aby w przeciwieństwie do efektów używania, należy `override` dodać następującą metodę do `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="510c4-136">`override`Modyfikator można dodać przed lub po `public` .</span><span class="sxs-lookup"><span data-stu-id="510c4-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="510c4-137">Dodaj `virtual` modyfikator do definicji elementu `Method1` w `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="510c4-138">`virtual`Modyfikator można dodać przed lub po `public` .</span><span class="sxs-lookup"><span data-stu-id="510c4-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="510c4-139">Uruchom ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="510c4-139">Run the project again.</span></span> <span data-ttu-id="510c4-140">Zwróć uwagę na szczególnie ostatnie dwa wiersze następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="510c4-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="510c4-141">Użycie `override` modyfikatora umożliwia dostęp do `bcdc` `Method1` metody, która jest zdefiniowana w `DerivedClass` .</span><span class="sxs-lookup"><span data-stu-id="510c4-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="510c4-142">Zwykle jest to wymagane zachowanie w hierarchiach dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="510c4-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="510c4-143">Obiekty mające wartości, które są tworzone na podstawie klasy pochodnej, są używane do używania metod, które są zdefiniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="510c4-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="510c4-144">To zachowanie można osiągnąć za pomocą polecenia, `override` Aby zwiększyć metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="510c4-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="510c4-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="510c4-145">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="510c4-146">Poniższy przykład ilustruje podobne zachowanie w innym kontekście.</span><span class="sxs-lookup"><span data-stu-id="510c4-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="510c4-147">W przykładzie zdefiniowano trzy klasy: Klasa bazowa o nazwie `Car` i dwie klasy, które są od niej pochodne `ConvertibleCar` i `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="510c4-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="510c4-148">Klasa bazowa zawiera `DescribeCar` metodę.</span><span class="sxs-lookup"><span data-stu-id="510c4-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="510c4-149">Metoda wyświetla podstawowy opis samochodu, a następnie wywołuje `ShowDetails` w celu podania dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="510c4-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="510c4-150">Każda z tych trzech klas definiuje `ShowDetails` metodę.</span><span class="sxs-lookup"><span data-stu-id="510c4-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="510c4-151">`new`Modyfikator służy do definiowania `ShowDetails` w `ConvertibleCar` klasie.</span><span class="sxs-lookup"><span data-stu-id="510c4-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="510c4-152">`override`Modyfikator służy do definiowania `ShowDetails` w `Minivan` klasie.</span><span class="sxs-lookup"><span data-stu-id="510c4-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="510c4-153">Przykład sprawdza, która wersja programu `ShowDetails` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="510c4-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="510c4-154">Poniższa metoda, `TestCars1` deklaruje wystąpienie każdej klasy, a następnie wywołuje `DescribeCar` każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="510c4-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="510c4-155">`TestCars1`tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="510c4-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="510c4-156">Zwróć uwagę na szczególnie wyniki dla `car2` , które prawdopodobnie nie są oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="510c4-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="510c4-157">Typ obiektu to `ConvertibleCar` , ale nie `DescribeCar` uzyskuje dostępu do wersji `ShowDetails` , która jest zdefiniowana w `ConvertibleCar` klasie, ponieważ ta metoda jest zadeklarowana z `new` modyfikatorem, a nie `override` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="510c4-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="510c4-158">W efekcie `ConvertibleCar` obiekt wyświetla ten sam opis, co `Car` obiekt.</span><span class="sxs-lookup"><span data-stu-id="510c4-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="510c4-159">Umożliwia odróżnienie wyników dla `car3` , które jest `Minivan` obiektem.</span><span class="sxs-lookup"><span data-stu-id="510c4-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="510c4-160">W tym przypadku metoda, `ShowDetails` która jest zadeklarowana w `Minivan` klasie przesłania `ShowDetails` metodę zadeklarowaną w `Car` klasie, a wyświetlany opis opisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="510c4-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="510c4-161">`TestCars2`tworzy listę obiektów, które mają typ `Car` .</span><span class="sxs-lookup"><span data-stu-id="510c4-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="510c4-162">Wartości obiektów są tworzone na podstawie `Car` `ConvertibleCar` klas,, i `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="510c4-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="510c4-163">`DescribeCar`jest wywoływana dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="510c4-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="510c4-164">Poniższy kod przedstawia definicję `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="510c4-164">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="510c4-165">Wyświetlane są następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="510c4-165">The following output is displayed.</span></span> <span data-ttu-id="510c4-166">Zwróć uwagę, że jest to taka sama jak wartość wyjściowa wyświetlana przez `TestCars1` .</span><span class="sxs-lookup"><span data-stu-id="510c4-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="510c4-167">`ShowDetails`Metoda `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, czy typ obiektu to `ConvertibleCar` , jak w `TestCars1` , lub `Car` , jak w `TestCars2` .</span><span class="sxs-lookup"><span data-stu-id="510c4-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="510c4-168">Odwrotnie, `car3` wywołuje `ShowDetails` metodę z `Minivan` klasy w obu przypadkach, niezależnie od tego, czy ma typ `Minivan` lub typ `Car` .</span><span class="sxs-lookup"><span data-stu-id="510c4-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="510c4-169">Metody `TestCars3` i `TestCars4` Dokończ przykład.</span><span class="sxs-lookup"><span data-stu-id="510c4-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="510c4-170">Metody te są wywoływane `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowanych jako typu `ConvertibleCar` i `Minivan` ( `TestCars3` ), a następnie z obiektów zadeklarowanych jako typu `Car` ( `TestCars4` ).</span><span class="sxs-lookup"><span data-stu-id="510c4-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="510c4-171">Poniższy kod definiuje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="510c4-171">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="510c4-172">Metody te generują następujące dane wyjściowe, które odpowiadają wynikom z pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="510c4-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="510c4-173">Poniższy kod przedstawia kompletny projekt i jego dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="510c4-173">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="510c4-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="510c4-174">See also</span></span>

- [<span data-ttu-id="510c4-175">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="510c4-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="510c4-176">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="510c4-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="510c4-177">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="510c4-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="510c4-178">base</span><span class="sxs-lookup"><span data-stu-id="510c4-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="510c4-179">streszczeń</span><span class="sxs-lookup"><span data-stu-id="510c4-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
