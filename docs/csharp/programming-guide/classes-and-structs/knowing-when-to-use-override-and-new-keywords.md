---
title: Zaznanie sytuacji, w których należy użyć C# przesłonięć i nowych słów kluczowych — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 00751cd8eac7979fe94d890ddeb7d13edb233f9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596474"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="30ac9-102">Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="30ac9-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="30ac9-103">W C#programie Metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="30ac9-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="30ac9-104">Możesz określić sposób działania metod przy użyciu słów kluczowych [New](../../language-reference/keywords/new-modifier.md) i [override](../../language-reference/keywords/override.md) .</span><span class="sxs-lookup"><span data-stu-id="30ac9-104">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="30ac9-105">`new` `virtual` Modyfikator rozszerza metodę klasy bazowej, a modyfikator ukrywa dostępną metodę klasy bazowej. `override`</span><span class="sxs-lookup"><span data-stu-id="30ac9-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="30ac9-106">Różnica przedstawiono w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="30ac9-107">W aplikacji konsoli Zadeklaruj poniższe dwie klasy `BaseClass` i. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="30ac9-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="30ac9-108">`DerivedClass`dziedziczy z `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-109">W metodzie Zadeklaruj zmienne `bc`, `dc`, i `bcdc`. `Main`</span><span class="sxs-lookup"><span data-stu-id="30ac9-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="30ac9-110">`bc`jest typu `BaseClass`, a jego wartość jest typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="30ac9-111">`dc`jest typu `DerivedClass`, a jego wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="30ac9-112">`bcdc`jest typu `BaseClass`, a jego wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="30ac9-113">Jest to zmienna, do której należy zwrócić uwagę.</span><span class="sxs-lookup"><span data-stu-id="30ac9-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="30ac9-114">Ze `bc` względu na `BaseClass`to, że i `bcdc` mają typ `Method1`, mogą oni jedynie bezpośrednio uzyskać dostęp, chyba że używasz rzutowania.</span><span class="sxs-lookup"><span data-stu-id="30ac9-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="30ac9-115">Zmienna `dc` ma dostęp do `Method1` obu `Method2`i.</span><span class="sxs-lookup"><span data-stu-id="30ac9-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="30ac9-116">Te relacje są pokazane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-117">Następnie Dodaj następującą `Method2` metodę do `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="30ac9-118">Podpis tej metody jest zgodny z podpisem `Method2` metody w. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="30ac9-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="30ac9-119">Ponieważ `BaseClass` `BaseClass` `bc` `bcdc`ma teraz metodę,możnadodaćdrugąinstrukcjęwywołującądlazmiennychi,jakpokazanowponiższymkodzie.`Method2`</span><span class="sxs-lookup"><span data-stu-id="30ac9-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="30ac9-120">Podczas kompilowania projektu, zobaczysz, że dodanie `Method2` metody w `BaseClass` powoduje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="30ac9-121">`Method2` Ostrzeżenie oznacza, że metoda w programie `DerivedClass` ukrywa `Method2` metodę w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="30ac9-122">Zaleca się użycie `new` słowa kluczowego w definicji, `Method2` Jeśli zamierzasz mieć ten wynik.</span><span class="sxs-lookup"><span data-stu-id="30ac9-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="30ac9-123">Alternatywnie można zmienić nazwę jednej z `Method2` metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktycznie możliwe.</span><span class="sxs-lookup"><span data-stu-id="30ac9-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="30ac9-124">Przed dodaniem `new`programu Uruchom program, aby zobaczyć dane wyjściowe generowane przez dodatkowe instrukcje wywoływania.</span><span class="sxs-lookup"><span data-stu-id="30ac9-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="30ac9-125">Zostaną wyświetlone następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="30ac9-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="30ac9-126">`new` Słowo kluczowe zachowuje relacje, które tworzą dane wyjściowe, ale pomija ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="30ac9-127">Zmienne, które mają typ `BaseClass` `BaseClass`, nadal uzyskują dostęp do elementów członkowskich, a zmienna, która `DerivedClass` ma typ, nadal uzyskuje dostęp do członków w `DerivedClass` pierwszej kolejności, a `BaseClass`następnie do rozważania członków dziedziczonych z.</span><span class="sxs-lookup"><span data-stu-id="30ac9-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="30ac9-128">Aby pominąć ostrzeżenie, Dodaj `new` modyfikator do `Method2` definicji w `DerivedClass`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="30ac9-129">Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="30ac9-130">Ponownie uruchom program, aby sprawdzić, czy dane wyjściowe nie uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="30ac9-131">Sprawdź również, czy ostrzeżenie nie jest już wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="30ac9-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="30ac9-132">Przy użyciu `new`, potwierdzasz, że użytkownik ma świadomość, że modyfikowany członek ukrywa element członkowski, który jest Dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="30ac9-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="30ac9-133">Aby uzyskać więcej informacji na temat ukrywania nazw poprzez dziedziczenie, zobacz [New modyfikator](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="30ac9-133">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="30ac9-134">Aby w przeciwieństwie do efektów używania `override`, należy dodać następującą metodę do. `DerivedClass`</span><span class="sxs-lookup"><span data-stu-id="30ac9-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="30ac9-135">Modyfikator można dodać przed lub po `public`. `override`</span><span class="sxs-lookup"><span data-stu-id="30ac9-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="30ac9-136">Dodaj modyfikator do definicji elementu `Method1` w `BaseClass`. `virtual`</span><span class="sxs-lookup"><span data-stu-id="30ac9-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="30ac9-137">Modyfikator można dodać przed lub po `public`. `virtual`</span><span class="sxs-lookup"><span data-stu-id="30ac9-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="30ac9-138">Uruchom projekt ponownie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-138">Run the project again.</span></span> <span data-ttu-id="30ac9-139">Zwróć uwagę na szczególnie ostatnie dwa wiersze następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="30ac9-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="30ac9-140">Użycie `override` modyfikatora umożliwia `bcdc` dostęp `Method1` do metody, która jest zdefiniowana w `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="30ac9-141">Zwykle jest to wymagane zachowanie w hierarchiach dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="30ac9-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="30ac9-142">Obiekty mające wartości, które są tworzone na podstawie klasy pochodnej, są używane do używania metod, które są zdefiniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="30ac9-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="30ac9-143">To zachowanie można osiągnąć za pomocą `override` polecenia, aby zwiększyć metodę klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="30ac9-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="30ac9-144">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="30ac9-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-145">Poniższy przykład ilustruje podobne zachowanie w innym kontekście.</span><span class="sxs-lookup"><span data-stu-id="30ac9-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="30ac9-146">W przykładzie zdefiniowano trzy klasy: Klasa bazowa o `Car` nazwie i dwie klasy, które są od `ConvertibleCar` niej pochodne `Minivan`i.</span><span class="sxs-lookup"><span data-stu-id="30ac9-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="30ac9-147">Klasa bazowa zawiera `DescribeCar` metodę.</span><span class="sxs-lookup"><span data-stu-id="30ac9-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="30ac9-148">Metoda wyświetla podstawowy opis samochodu, a następnie wywołuje `ShowDetails` w celu podania dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="30ac9-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="30ac9-149">Każda z tych trzech klas definiuje `ShowDetails` metodę.</span><span class="sxs-lookup"><span data-stu-id="30ac9-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="30ac9-150">Modyfikator służy do definiowania `ShowDetails` w `ConvertibleCar` klasie. `new`</span><span class="sxs-lookup"><span data-stu-id="30ac9-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="30ac9-151">Modyfikator służy do definiowania `ShowDetails` w `Minivan` klasie. `override`</span><span class="sxs-lookup"><span data-stu-id="30ac9-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-152">Przykład sprawdza, która wersja programu `ShowDetails` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="30ac9-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="30ac9-153">Poniższa metoda, `TestCars1`deklaruje wystąpienie każdej klasy, a następnie wywołuje `DescribeCar` każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-154">`TestCars1`tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="30ac9-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="30ac9-155">Zwróć uwagę na szczególnie wyniki `car2`dla, które prawdopodobnie nie są oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="30ac9-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="30ac9-156">Typ `ConvertibleCar`obiektu to, ale `DescribeCar` nie uzyskuje dostępu do wersji `ShowDetails` , która jest zdefiniowana w `ConvertibleCar` klasie, `override` ponieważ ta metoda jest zadeklarowana z `new` modyfikatorem, a nie modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="30ac9-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="30ac9-157">W efekcie `ConvertibleCar` obiekt wyświetla ten sam opis, `Car` co obiekt.</span><span class="sxs-lookup"><span data-stu-id="30ac9-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="30ac9-158">Umożliwia odróżnienie `car3`wyników dla, które `Minivan` jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="30ac9-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="30ac9-159">W tym przypadku `ShowDetails` Metoda, która jest zadeklarowana `Minivan` w klasie przesłania `ShowDetails` metodę zadeklarowaną w `Car` klasie, a wyświetlany opis opisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="30ac9-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-160">`TestCars2`tworzy listę obiektów, które mają typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="30ac9-161">Wartości obiektów są tworzone na podstawie `Car`klas, `ConvertibleCar`, i `Minivan` .</span><span class="sxs-lookup"><span data-stu-id="30ac9-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="30ac9-162">`DescribeCar`jest wywoływana dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="30ac9-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="30ac9-163">Poniższy kod przedstawia definicję `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="30ac9-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-164">Wyświetlane są następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="30ac9-164">The following output is displayed.</span></span> <span data-ttu-id="30ac9-165">Zwróć uwagę, że jest to taka sama jak wartość wyjściowa wyświetlana `TestCars1`przez.</span><span class="sxs-lookup"><span data-stu-id="30ac9-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="30ac9-166">`TestCars1` `ConvertibleCar` `Car` `TestCars2`Metoda klasy nie jest wywoływana, niezależnie od tego, czy typ obiektu to, jak w, lub, jak w. `ConvertibleCar` `ShowDetails`</span><span class="sxs-lookup"><span data-stu-id="30ac9-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="30ac9-167">Odwrotnie `car3` , wywołuje `ShowDetails` metodę z `Minivan` klasy w obu przypadkach, niezależnie od tego, czy `Minivan` ma typ `Car`lub typ.</span><span class="sxs-lookup"><span data-stu-id="30ac9-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-168">Metody `TestCars3` i`TestCars4` Dokończ przykład.</span><span class="sxs-lookup"><span data-stu-id="30ac9-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="30ac9-169">Metody te są `ShowDetails` wywoływane bezpośrednio, najpierw z obiektów zadeklarowanych jako `ConvertibleCar` typu `Minivan` i`TestCars3`(), a następnie z obiektów zadeklarowanych `Car` jako`TestCars4`typu ().</span><span class="sxs-lookup"><span data-stu-id="30ac9-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="30ac9-170">Poniższy kod definiuje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="30ac9-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-171">Metody te generują następujące dane wyjściowe, które odpowiadają wynikom z pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="30ac9-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="30ac9-172">Poniższy kod przedstawia kompletny projekt i jego dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="30ac9-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30ac9-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30ac9-173">See also</span></span>

- [<span data-ttu-id="30ac9-174">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="30ac9-174">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="30ac9-175">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="30ac9-175">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="30ac9-176">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="30ac9-176">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="30ac9-177">base</span><span class="sxs-lookup"><span data-stu-id="30ac9-177">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="30ac9-178">abstract</span><span class="sxs-lookup"><span data-stu-id="30ac9-178">abstract</span></span>](../../language-reference/keywords/abstract.md)
