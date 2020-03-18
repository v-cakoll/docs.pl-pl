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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="792b6-102">Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="792b6-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="792b6-103">W języku C#metoda w klasie pochodnej może mieć taką samą nazwę jak metoda w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="792b6-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="792b6-104">Można określić, jak metody współdziałają przy użyciu [nowych](../../language-reference/keywords/new-modifier.md) i [zastąpić](../../language-reference/keywords/override.md) słowa kluczowe.</span><span class="sxs-lookup"><span data-stu-id="792b6-104">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="792b6-105">Modyfikator `override` *rozszerza* metodę `virtual` klasy podstawowej, a `new` modyfikator *ukrywa* metodę dostępnej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="792b6-105">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="792b6-106">Różnica jest zilustrowana w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="792b6-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="792b6-107">W aplikacji konsoli zadeklarować następujące `BaseClass` dwie `DerivedClass`klasy i .</span><span class="sxs-lookup"><span data-stu-id="792b6-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="792b6-108">`DerivedClass`dziedziczy `BaseClass`z .</span><span class="sxs-lookup"><span data-stu-id="792b6-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="792b6-109">W `Main` metodzie deklaruj `bc`zmienne , `dc`i `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="792b6-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="792b6-110">`bc`jest typu, `BaseClass`a jego wartość `BaseClass`jest typu .</span><span class="sxs-lookup"><span data-stu-id="792b6-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="792b6-111">`dc`jest typu, `DerivedClass`a jego wartość `DerivedClass`jest typu .</span><span class="sxs-lookup"><span data-stu-id="792b6-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="792b6-112">`bcdc`jest typu, `BaseClass`a jego wartość `DerivedClass`jest typu .</span><span class="sxs-lookup"><span data-stu-id="792b6-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="792b6-113">Jest to zmienna, na jaką należy zwrócić uwagę.</span><span class="sxs-lookup"><span data-stu-id="792b6-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="792b6-114">Ponieważ `bc` `bcdc` i `BaseClass`mają typ , `Method1`mogą uzyskać bezpośredni dostęp , chyba że używasz odlewania.</span><span class="sxs-lookup"><span data-stu-id="792b6-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="792b6-115">Zmienna `dc` może `Method1` `Method2`uzyskać dostęp do obu i .</span><span class="sxs-lookup"><span data-stu-id="792b6-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="792b6-116">Te relacje są wyświetlane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="792b6-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="792b6-117">Następnie dodaj `Method2` następującą `BaseClass`metodę do .</span><span class="sxs-lookup"><span data-stu-id="792b6-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="792b6-118">Podpis tej metody jest zgodny `Method2` z `DerivedClass`podpisem metody w pliku .</span><span class="sxs-lookup"><span data-stu-id="792b6-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="792b6-119">Ponieważ `BaseClass` teraz `Method2` ma metodę, można dodać drugą `BaseClass` instrukcję wywołującą dla zmiennych `bc` i `bcdc`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="792b6-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="792b6-120">Podczas tworzenia projektu, widać, że dodanie `Method2` metody `BaseClass` powoduje ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="792b6-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="792b6-121">Ostrzeżenie mówi, `Method2` że `DerivedClass` metoda w `Method2` ukrywa `BaseClass`metodę w .</span><span class="sxs-lookup"><span data-stu-id="792b6-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="792b6-122">Zaleca się użycie `new` słowa kluczowego w `Method2` definicji, jeśli zamierzasz spowodować ten wynik.</span><span class="sxs-lookup"><span data-stu-id="792b6-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="792b6-123">Alternatywnie można zmienić nazwę jednej `Method2` z metod, aby rozwiązać ostrzeżenie, ale nie zawsze jest to praktyczne.</span><span class="sxs-lookup"><span data-stu-id="792b6-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="792b6-124">Przed `new`dodaniem uruchom program, aby wyświetlić dane wyjściowe wytwarzane przez dodatkowe instrukcje wywołujące.</span><span class="sxs-lookup"><span data-stu-id="792b6-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="792b6-125">Zostaną wyświetlone następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="792b6-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="792b6-126">Słowo `new` kluczowe zachowuje relacje, które produkują, że dane wyjściowe, ale pomija ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="792b6-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="792b6-127">Zmienne, które mają `BaseClass` typ, nadal `BaseClass`uzyskują dostęp do `DerivedClass` elementów członkowskich , `DerivedClass` a zmienna, która ma `BaseClass`typ, nadal uzyskuje dostęp do elementów członkowskich w pierwszej kolejności, a następnie do rozważenia członków dziedziczonych z .</span><span class="sxs-lookup"><span data-stu-id="792b6-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="792b6-128">Aby pominąć ostrzeżenie, `new` dodaj modyfikator do definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="792b6-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="792b6-129">Modyfikator można dodać `public`przed lub po .</span><span class="sxs-lookup"><span data-stu-id="792b6-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="792b6-130">Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="792b6-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="792b6-131">Sprawdź również, czy ostrzeżenie nie jest już wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="792b6-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="792b6-132">Za `new`pomocą , potwierdzasz, że są świadomi, że element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczony z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="792b6-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="792b6-133">Aby uzyskać więcej informacji na temat ukrywania nazw w dziedziczeniu, zobacz [nowy modyfikator](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="792b6-133">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="792b6-134">Aby porównać to zachowanie z `override`efektami używania, `DerivedClass`dodaj następującą metodę do .</span><span class="sxs-lookup"><span data-stu-id="792b6-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="792b6-135">Modyfikator `override` można dodać `public`przed lub po .</span><span class="sxs-lookup"><span data-stu-id="792b6-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="792b6-136">Dodaj `virtual` modyfikator do `Method1` `BaseClass`definicji w .</span><span class="sxs-lookup"><span data-stu-id="792b6-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="792b6-137">Modyfikator `virtual` można dodać `public`przed lub po .</span><span class="sxs-lookup"><span data-stu-id="792b6-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="792b6-138">Uruchom ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="792b6-138">Run the project again.</span></span> <span data-ttu-id="792b6-139">Zwróć uwagę zwłaszcza na ostatnie dwa wiersze następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="792b6-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="792b6-140">Użycie `override` modyfikatora `bcdc` umożliwia `Method1` dostęp do metody `DerivedClass`zdefiniowanej w programie .</span><span class="sxs-lookup"><span data-stu-id="792b6-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="792b6-141">Zazwyczaj jest to pożądane zachowanie w hierarchiach dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="792b6-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="792b6-142">Chcesz, aby obiekty, które mają wartości, które są tworzone z klasy pochodnej, aby użyć metod, które są zdefiniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="792b6-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="792b6-143">Można osiągnąć to `override` zachowanie przy użyciu rozszerzenia metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="792b6-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="792b6-144">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="792b6-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="792b6-145">Poniższy przykład ilustruje podobne zachowanie w innym kontekście.</span><span class="sxs-lookup"><span data-stu-id="792b6-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="792b6-146">W przykładzie zdefiniowano trzy klasy: klasę podstawową o `Car` nazwie `ConvertibleCar` `Minivan`i dwie klasy, które pochodzą z niego i .</span><span class="sxs-lookup"><span data-stu-id="792b6-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="792b6-147">Klasa podstawowa `DescribeCar` zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="792b6-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="792b6-148">Metoda wyświetla podstawowy opis samochodu, a `ShowDetails` następnie wywołuje dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="792b6-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="792b6-149">Każda z trzech klas `ShowDetails` definiuje metodę.</span><span class="sxs-lookup"><span data-stu-id="792b6-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="792b6-150">Modyfikator `new` służy `ShowDetails` do `ConvertibleCar` definiowania w klasie.</span><span class="sxs-lookup"><span data-stu-id="792b6-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="792b6-151">Modyfikator `override` służy `ShowDetails` do `Minivan` definiowania w klasie.</span><span class="sxs-lookup"><span data-stu-id="792b6-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="792b6-152">Przykład testuje, `ShowDetails` która wersja jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="792b6-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="792b6-153">Następująca metoda `TestCars1`, deklaruje wystąpienie każdej klasy, `DescribeCar` a następnie wywołuje każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="792b6-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="792b6-154">`TestCars1`wytwarza następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="792b6-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="792b6-155">Zwróć uwagę `car2`zwłaszcza na wyniki dla , które prawdopodobnie nie są to, czego się spodziewałeś.</span><span class="sxs-lookup"><span data-stu-id="792b6-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="792b6-156">Typ `ConvertibleCar`obiektu jest , `DescribeCar` ale nie ma `ShowDetails` dostępu do wersji, `ConvertibleCar` która jest zdefiniowana `new` w klasie, `override` ponieważ ta metoda jest zadeklarowana za pomocą modyfikatora, a nie modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="792b6-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="792b6-157">W rezultacie `ConvertibleCar` obiekt wyświetla ten sam `Car` opis jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="792b6-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="792b6-158">Kontrast wyniki `car3`dla , `Minivan` który jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="792b6-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="792b6-159">W takim przypadku `ShowDetails` metoda, która `Minivan` jest zadeklarowana `ShowDetails` w klasie zastępuje `Car` metodę, która jest zadeklarowana w klasie, a opis, który jest wyświetlany opisuje minivan.</span><span class="sxs-lookup"><span data-stu-id="792b6-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="792b6-160">`TestCars2`tworzy listę obiektów, które `Car`mają typ .</span><span class="sxs-lookup"><span data-stu-id="792b6-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="792b6-161">Wartości obiektów są tworzone z `Car`, `ConvertibleCar`i `Minivan` klas.</span><span class="sxs-lookup"><span data-stu-id="792b6-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="792b6-162">`DescribeCar`jest wywoływana na każdym elemencie listy.</span><span class="sxs-lookup"><span data-stu-id="792b6-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="792b6-163">Poniższy kod przedstawia definicję . `TestCars2`</span><span class="sxs-lookup"><span data-stu-id="792b6-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="792b6-164">Zostanie wyświetlone następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="792b6-164">The following output is displayed.</span></span> <span data-ttu-id="792b6-165">Należy zauważyć, że jest taka sama jak `TestCars1`dane wyjściowe, które są wyświetlane przez .</span><span class="sxs-lookup"><span data-stu-id="792b6-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="792b6-166">Metoda `ShowDetails` `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, `ConvertibleCar`czy typ `TestCars1`obiektu `Car`jest `TestCars2`, jak w , lub , jak w .</span><span class="sxs-lookup"><span data-stu-id="792b6-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="792b6-167">I `car3` odwrotnie `ShowDetails` wywołuje metodę `Minivan` z klasy w obu `Minivan` przypadkach, `Car`czy ma typ lub typ .</span><span class="sxs-lookup"><span data-stu-id="792b6-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="792b6-168">Metody `TestCars3` i `TestCars4` wypełnić przykład.</span><span class="sxs-lookup"><span data-stu-id="792b6-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="792b6-169">Te metody `ShowDetails` wywołać bezpośrednio, najpierw z `ConvertibleCar` `Minivan` obiektów`TestCars3`zadeklarowanych jako typ `Car` i`TestCars4`( ), a następnie z obiektów zadeklarowanych jako typu ( ).</span><span class="sxs-lookup"><span data-stu-id="792b6-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="792b6-170">Poniższy kod definiuje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="792b6-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="792b6-171">Metody dają następujące dane wyjściowe, co odpowiada wynikom z pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="792b6-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="792b6-172">Poniższy kod przedstawia cały projekt i jego dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="792b6-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="792b6-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="792b6-173">See also</span></span>

- [<span data-ttu-id="792b6-174">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="792b6-174">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="792b6-175">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="792b6-175">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="792b6-176">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="792b6-176">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="792b6-177">base</span><span class="sxs-lookup"><span data-stu-id="792b6-177">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="792b6-178">Abstrakcja</span><span class="sxs-lookup"><span data-stu-id="792b6-178">abstract</span></span>](../../language-reference/keywords/abstract.md)
