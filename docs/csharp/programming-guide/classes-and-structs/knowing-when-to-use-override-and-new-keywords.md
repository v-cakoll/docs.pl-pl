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
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="936ee-102">Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="936ee-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="936ee-103">W języku C# metody w klasie pochodnej może mieć taką samą nazwę jak metody w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="936ee-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="936ee-104">Można określić sposób interakcji metody przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) i [zastąpienia](../../../csharp/language-reference/keywords/override.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="936ee-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="936ee-105">`override` Modyfikator *rozszerza* metody klasy podstawowej i `new` modyfikator *ukrywa* go.</span><span class="sxs-lookup"><span data-stu-id="936ee-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="936ee-106">Różnice przedstawiono w przykładach w niniejszym temacie.</span><span class="sxs-lookup"><span data-stu-id="936ee-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="936ee-107">W aplikacji konsoli, należy zadeklarować następujące dwie klasy `BaseClass` i `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="936ee-108">`DerivedClass` dziedziczy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="936ee-109">W `Main` metody, Zadeklaruj zmienne `bc`, `dc`, i `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="936ee-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
-   <span data-ttu-id="936ee-110">`bc` Typ jest `BaseClass`, a jego wartość jest typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
-   <span data-ttu-id="936ee-111">`dc` Typ jest `DerivedClass`, a jego wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
-   <span data-ttu-id="936ee-112">`bcdc` Typ jest `BaseClass`, a jego wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="936ee-113">Jest to zmienna, aby zwrócić uwagę na.</span><span class="sxs-lookup"><span data-stu-id="936ee-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="936ee-114">Ponieważ `bc` i `bcdc` ma typ `BaseClass`, tylko bezpośrednio uzyskać dostęp do `Method1`, chyba że używasz rzutowania.</span><span class="sxs-lookup"><span data-stu-id="936ee-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="936ee-115">Zmienna `dc` dostęp zarówno do `Method1` i `Method2`.</span><span class="sxs-lookup"><span data-stu-id="936ee-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="936ee-116">Te relacje są wyświetlane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="936ee-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="936ee-117">Następnie dodaj następujące `Method2` metodę `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="936ee-118">Podpis tej metody pasuje do podpisu `Method2` metoda `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="936ee-119">Ponieważ `BaseClass` ma teraz `Method2` metody, druga instrukcja wywoływania można dodać do `BaseClass` zmienne `bc` i `bcdc`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="936ee-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="936ee-120">Podczas kompilowania projektu widać, że dodanie `Method2` metoda `BaseClass` powoduje, że ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="936ee-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="936ee-121">Komunikat ostrzeżenia, że `Method2` metody w `DerivedClass` ukrywa `Method2` metoda `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="936ee-122">Zaleca się używania `new` — słowo kluczowe w `Method2` definicji, jeśli zamierzasz spowodować tego wyniku.</span><span class="sxs-lookup"><span data-stu-id="936ee-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="936ee-123">Alternatywnie można zmienić nazwę jednej z `Method2` metody umożliwiające rozwiązanie to ostrzeżenie, ale nie jest zawsze praktyczne.</span><span class="sxs-lookup"><span data-stu-id="936ee-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="936ee-124">Przed dodaniem `new`, uruchom program, aby zobaczyć dane wyjściowe, generowane przez dodatkowe instrukcje wywołującego.</span><span class="sxs-lookup"><span data-stu-id="936ee-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="936ee-125">Następujące wyniki są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="936ee-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="936ee-126">`new` — Słowo kluczowe chroni relacje, które wywołują te dane wyjściowe, ale jego pominięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="936ee-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="936ee-127">Zmienne, które mają typ `BaseClass` dostęp do elementów członkowskich w dalszym ciągu `BaseClass`i zmienna, która ma typ `DerivedClass` w dalszym ciągu dostęp do elementów członkowskich w `DerivedClass` pierwszy, a następnie należy wziąć pod uwagę członków dziedziczonych po elemencie `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="936ee-128">Aby pominąć to ostrzeżenie, Dodaj `new` modyfikator do definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="936ee-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="936ee-129">Modyfikator mogą być dodawane przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="936ee-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="936ee-130">Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie uległy zmianie.</span><span class="sxs-lookup"><span data-stu-id="936ee-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="936ee-131">Sprawdź także, czy ostrzeżenia nie będzie już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="936ee-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="936ee-132">Za pomocą `new`, są potwierdzające, że masz świadomość, że element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczona z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="936ee-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="936ee-133">Aby uzyskać więcej informacji o nazwie ukrywanie poprzez dziedziczenie, zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="936ee-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="936ee-134">Natomiast takie zachowanie skutki za pomocą do `override`, dodaj następującą metodę do `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="936ee-135">`override` Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="936ee-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="936ee-136">Dodaj `virtual` modyfikator do definicji `Method1` w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="936ee-137">`virtual` Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="936ee-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="936ee-138">Uruchom ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="936ee-138">Run the project again.</span></span> <span data-ttu-id="936ee-139">Zwróć uwagę szczególnie ostatnie dwa wiersze następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="936ee-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="936ee-140">Korzystanie z `override` umożliwia modyfikator `bcdc` dostępu `Method1` metodę, która jest zdefiniowana w `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="936ee-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="936ee-141">Zazwyczaj jest to zachowanie w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="936ee-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="936ee-142">Chcesz obiektów, które mają wartości, które są tworzone na podstawie klasy pochodnej w celu użycia metody, które są zdefiniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="936ee-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="936ee-143">To zachowanie można osiągnąć za pomocą `override` rozszerzenie metody klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="936ee-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="936ee-144">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="936ee-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="936ee-145">Poniższy przykład przedstawia podobne zachowanie w kontekście innej.</span><span class="sxs-lookup"><span data-stu-id="936ee-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="936ee-146">W przykładzie zdefiniowano trzech klas: klasa podstawowa o nazwie `Car` i dwie klasy, które są pochodnymi, `ConvertibleCar` i `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="936ee-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="936ee-147">Klasa podstawowa zawiera `DescribeCar` metody.</span><span class="sxs-lookup"><span data-stu-id="936ee-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="936ee-148">Metoda zawiera opis podstawowych samochodu, a następnie wywołuje `ShowDetails` o podanie dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="936ee-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="936ee-149">Definiuje trzy klas `ShowDetails` metody.</span><span class="sxs-lookup"><span data-stu-id="936ee-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="936ee-150">`new` Modyfikator służy do definiowania `ShowDetails` w `ConvertibleCar` klasy.</span><span class="sxs-lookup"><span data-stu-id="936ee-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="936ee-151">`override` Modyfikator służy do definiowania `ShowDetails` w `Minivan` klasy.</span><span class="sxs-lookup"><span data-stu-id="936ee-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="936ee-152">Przykład sprawdza wersję `ShowDetails` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="936ee-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="936ee-153">Następujące metody `TestCars1`, deklaruje wystąpienia każdej klasy, a następnie wywołuje `DescribeCar` na każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="936ee-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="936ee-154">`TestCars1` tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="936ee-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="936ee-155">Zwróć uwagę, szczególnie wyniki dla `car2`, które są prawdopodobnie niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="936ee-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="936ee-156">Typ obiektu jest `ConvertibleCar`, ale `DescribeCar` nie dostępu do wersji `ShowDetails` zdefiniowanego w `ConvertibleCar` klasy, ponieważ ta metoda jest zadeklarowany za pomocą `new` modyfikator, nie `override` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="936ee-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="936ee-157">W związku z tym `ConvertibleCar` obiekt wyświetla ten sam opis co `Car` obiektu.</span><span class="sxs-lookup"><span data-stu-id="936ee-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="936ee-158">Natomiast wyników dla `car3`, która jest `Minivan` obiektu.</span><span class="sxs-lookup"><span data-stu-id="936ee-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="936ee-159">W takim przypadku `ShowDetails` metodę, która jest zadeklarowana w `Minivan` klasy zastąpienia `ShowDetails` metodę, która jest zadeklarowana w `Car` klasy i opis, który jest wyświetlany w tym artykule opisano Mały furgon.</span><span class="sxs-lookup"><span data-stu-id="936ee-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="936ee-160">`TestCars2` Tworzy listę obiektów, które mają typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="936ee-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="936ee-161">Wartości te obiekty są utworzone z `Car`, `ConvertibleCar`, i `Minivan` klasy.</span><span class="sxs-lookup"><span data-stu-id="936ee-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="936ee-162">`DescribeCar` jest wywoływana dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="936ee-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="936ee-163">Poniższy kod przedstawia definicję `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="936ee-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="936ee-164">Następujące dane wyjściowe są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="936ee-164">The following output is displayed.</span></span> <span data-ttu-id="936ee-165">Zwróć uwagę, że jest taka sama jak dane wyjściowe, który jest wyświetlany za `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="936ee-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="936ee-166">`ShowDetails` Metody `ConvertibleCar` klasy nie zostanie wywołany, niezależnie od tego, czy typ obiektu `ConvertibleCar`, jak w `TestCars1`, lub `Car`, jak w `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="936ee-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="936ee-167">Z drugiej strony `car3` wywołania `ShowDetails` metody z `Minivan` klasy w obu przypadkach, czy ma typ `Minivan` lub typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="936ee-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="936ee-168">Metody `TestCars3` i `TestCars4` ukończyć przykład.</span><span class="sxs-lookup"><span data-stu-id="936ee-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="936ee-169">Te metody mogą wywoływać `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowany typ `ConvertibleCar` i `Minivan` (`TestCars3`), następnie z obiektów zadeklarowany typ `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="936ee-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="936ee-170">Poniższy kod definiuje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="936ee-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="936ee-171">Te metody powodują następujące dane wyjściowe, co odpowiada wyników z pierwszego przykładu, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="936ee-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="936ee-172">Poniższy kod przedstawia kompletnego projektu i jego dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="936ee-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="936ee-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="936ee-173">See Also</span></span>  
 [<span data-ttu-id="936ee-174">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="936ee-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="936ee-175">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="936ee-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="936ee-176">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="936ee-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="936ee-177">base</span><span class="sxs-lookup"><span data-stu-id="936ee-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="936ee-178">abstract</span><span class="sxs-lookup"><span data-stu-id="936ee-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
