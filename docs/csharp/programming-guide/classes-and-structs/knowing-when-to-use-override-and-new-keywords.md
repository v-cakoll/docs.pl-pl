---
title: Użycie przesłonięć i nowych słów kluczowych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: b1d99b0c5241a99ba7f621faff7c39d20776b2ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496260"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="c2788-102">Użycie przesłonięć i nowych słów kluczowych (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c2788-102">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="c2788-103">W języku C# metody w klasie pochodnej może mieć taką samą nazwę jak metody w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="c2788-103">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="c2788-104">Można określić sposób interakcji metody przy użyciu [nowe](../../../csharp/language-reference/keywords/new.md) i [zastąpienia](../../../csharp/language-reference/keywords/override.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="c2788-104">You can specify how the methods interact by using the [new](../../../csharp/language-reference/keywords/new.md) and [override](../../../csharp/language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="c2788-105">`override` Modyfikator *rozszerza* metody klasy bazowej i `new` modyfikator *ukrywa* go.</span><span class="sxs-lookup"><span data-stu-id="c2788-105">The `override` modifier *extends* the base class method, and the `new` modifier *hides* it.</span></span> <span data-ttu-id="c2788-106">Różnica jest przedstawionych w przykładach w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c2788-106">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="c2788-107">W aplikacji konsoli, należy zadeklarować następujące dwie klasy `BaseClass` i `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-107">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="c2788-108">`DerivedClass` dziedziczy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-108">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
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
  
 <span data-ttu-id="c2788-109">W `Main` metody deklarować zmienne `bc`, `dc`, i `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="c2788-109">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
-   <span data-ttu-id="c2788-110">`bc` Typ jest `BaseClass`, a jej wartość jest typu `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-110">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
-   <span data-ttu-id="c2788-111">`dc` Typ jest `DerivedClass`, a jej wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-111">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
-   <span data-ttu-id="c2788-112">`bcdc` Typ jest `BaseClass`, a jej wartość jest typu `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-112">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="c2788-113">Jest to zmienna, na które należy zwrócić uwagę.</span><span class="sxs-lookup"><span data-stu-id="c2788-113">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="c2788-114">Ponieważ `bc` i `bcdc` typ `BaseClass`, tylko bezpośrednio uzyskać dostęp do `Method1`, chyba że używasz rzutowania.</span><span class="sxs-lookup"><span data-stu-id="c2788-114">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="c2788-115">Zmienna `dc` dostęp zarówno do `Method1` i `Method2`.</span><span class="sxs-lookup"><span data-stu-id="c2788-115">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="c2788-116">Te relacje są wyświetlane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c2788-116">These relationships are shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="c2788-117">Następnie dodaj następujące `Method2` metody `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-117">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="c2788-118">Podpis tej metody pasuje do podpisu `Method2` method in Class metoda `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-118">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="c2788-119">Ponieważ `BaseClass` ma teraz `Method2` metody, druga instrukcja wywołującego można dodać `BaseClass` zmienne `bc` i `bcdc`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c2788-119">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="c2788-120">Podczas tworzenia projektu, zobaczysz, że dodanie `Method2` method in Class metoda `BaseClass` powoduje, że ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="c2788-120">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="c2788-121">To ostrzeżenie jest wyświetlany komunikat, który `Method2` method in Class metoda `DerivedClass` ukrywa `Method2` method in Class metoda `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-121">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="c2788-122">Zaleca się używać `new` — słowo kluczowe w `Method2` definicji, jeśli zamierzasz spowodować, że wynik.</span><span class="sxs-lookup"><span data-stu-id="c2788-122">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="c2788-123">Alternatywnie, można zmienić nazwę jednej z `Method2` metody umożliwiające rozwiązanie to ostrzeżenie, ale nie jest zawsze możliwe.</span><span class="sxs-lookup"><span data-stu-id="c2788-123">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="c2788-124">Przed dodaniem `new`, uruchom program, aby wyświetlić dane wyjściowe generowane przez dodatkowe instrukcje wywoływania.</span><span class="sxs-lookup"><span data-stu-id="c2788-124">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="c2788-125">Są wyświetlane następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="c2788-125">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="c2788-126">`new` — Słowo kluczowe chroni relacje, które tworzą te dane wyjściowe, ale jej umożliwia pominięcie ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="c2788-126">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="c2788-127">Zmienne, które mają typ `BaseClass` w dalszym ciągu uzyskać dostęp do składowych aspektów `BaseClass`i zmienna, która ma typ `DerivedClass` w dalszym ciągu dostęp do elementów członkowskich w `DerivedClass` pierwszy, a następnie należy wziąć pod uwagę członków dziedziczonych po elemencie `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-127">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="c2788-128">Aby pominąć to ostrzeżenie, należy dodać `new` modyfikatora definicji `Method2` w `DerivedClass`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c2788-128">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="c2788-129">Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="c2788-129">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="c2788-130">Uruchom program ponownie, aby sprawdzić, czy dane wyjściowe nie zmienił się.</span><span class="sxs-lookup"><span data-stu-id="c2788-130">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="c2788-131">Sprawdź także, że ostrzeżenie nie jest już wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="c2788-131">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="c2788-132">Za pomocą `new`, są potwierdzające, że masz świadomość, element członkowski, który modyfikuje ukrywa element członkowski, który jest dziedziczony z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c2788-132">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="c2788-133">Aby uzyskać więcej informacji na temat ukrywanie nazw poprzez dziedziczenie, zobacz [new — modyfikator](../../../csharp/language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="c2788-133">For more information about name hiding through inheritance, see [new Modifier](../../../csharp/language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="c2788-134">Natomiast takie zachowanie do efektów do `override`, dodaj następującą metodę do `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-134">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="c2788-135">`override` Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="c2788-135">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="c2788-136">Dodaj `virtual` modyfikatora definicji `Method1` w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-136">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="c2788-137">`virtual` Modyfikator można dodać przed lub po `public`.</span><span class="sxs-lookup"><span data-stu-id="c2788-137">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="c2788-138">Uruchom projekt ponownie.</span><span class="sxs-lookup"><span data-stu-id="c2788-138">Run the project again.</span></span> <span data-ttu-id="c2788-139">Zwróć uwagę, szczególnie ostatnie dwa wiersze następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c2788-139">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="c2788-140">Korzystanie z `override` modyfikator umożliwia `bcdc` dostęp do `Method1` metodę, która jest zdefiniowana w `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="c2788-140">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="c2788-141">Zazwyczaj jest to żądane zachowanie w hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="c2788-141">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="c2788-142">Chcesz, aby obiekty, które mają wartości, które są tworzone na podstawie klasy pochodnej w celu użycia metod, które są zdefiniowane w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="c2788-142">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="c2788-143">To zachowanie można osiągnąć za pomocą `override` rozszerzenie metody klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c2788-143">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="c2788-144">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="c2788-144">The following code contains the full example.</span></span>  
  
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
  
 <span data-ttu-id="c2788-145">Poniższy przykład ilustruje podobne zachowanie w innym kontekście.</span><span class="sxs-lookup"><span data-stu-id="c2788-145">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="c2788-146">W przykładzie zdefiniowano trzech klas: klasa bazowa o nazwie `Car` i dwie klasy, które są uzyskiwane z nich, `ConvertibleCar` i `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="c2788-146">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="c2788-147">Klasa bazowa zawiera `DescribeCar` metody.</span><span class="sxs-lookup"><span data-stu-id="c2788-147">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="c2788-148">Metoda zawiera podstawowy opis metodyki samochód, a następnie wywołuje `ShowDetails` dostarczenie dodatkowych informacji.</span><span class="sxs-lookup"><span data-stu-id="c2788-148">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="c2788-149">Każdy z trzech klas definiuje `ShowDetails` metody.</span><span class="sxs-lookup"><span data-stu-id="c2788-149">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="c2788-150">`new` Modyfikator jest używany do definiowania `ShowDetails` w `ConvertibleCar` klasy.</span><span class="sxs-lookup"><span data-stu-id="c2788-150">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="c2788-151">`override` Modyfikator jest używany do definiowania `ShowDetails` w `Minivan` klasy.</span><span class="sxs-lookup"><span data-stu-id="c2788-151">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
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
  
 <span data-ttu-id="c2788-152">Przykład sprawdza wersję `ShowDetails` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c2788-152">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="c2788-153">Następującą metodę `TestCars1`, deklaruje wystąpienia każdej klasy, a następnie wywołuje `DescribeCar` w każdym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="c2788-153">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
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
  
 <span data-ttu-id="c2788-154">`TestCars1` generuje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="c2788-154">`TestCars1` produces the following output.</span></span> <span data-ttu-id="c2788-155">Zwróć uwagę, szczególnie wyniki `car2`, które są prawdopodobnie niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="c2788-155">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="c2788-156">Typ obiektu jest `ConvertibleCar`, ale `DescribeCar` nie uzyskać dostępu do wersji `ShowDetails` zdefiniowanego w `ConvertibleCar` klasy, ponieważ ta metoda jest zadeklarowana za pomocą `new` modyfikator, nie `override` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="c2788-156">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="c2788-157">W rezultacie `ConvertibleCar` obiekt wyświetla ten sam opis co `Car` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c2788-157">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="c2788-158">Porównaj wyniki `car3`, czyli `Minivan` obiektu.</span><span class="sxs-lookup"><span data-stu-id="c2788-158">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="c2788-159">W tym przypadku `ShowDetails` metodę, która jest zadeklarowana w `Minivan` klasy zastąpienia `ShowDetails` metodę, która jest zadeklarowana w `Car` klasy i opis, który jest wyświetlany w tym artykule opisano Mały furgon.</span><span class="sxs-lookup"><span data-stu-id="c2788-159">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
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
  
 <span data-ttu-id="c2788-160">`TestCars2` Tworzy listę obiektów, które mają typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="c2788-160">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="c2788-161">Wartości, które obiekty są tworzone z `Car`, `ConvertibleCar`, i `Minivan` klasy.</span><span class="sxs-lookup"><span data-stu-id="c2788-161">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="c2788-162">`DescribeCar` jest wywoływana dla każdego elementu listy.</span><span class="sxs-lookup"><span data-stu-id="c2788-162">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="c2788-163">Poniższy kod przedstawia definicję `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="c2788-163">The following code shows the definition of `TestCars2`.</span></span>  
  
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
  
 <span data-ttu-id="c2788-164">Następujące dane wyjściowe są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="c2788-164">The following output is displayed.</span></span> <span data-ttu-id="c2788-165">Zauważ, że jest taki sam jak wynik wyświetlony po `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="c2788-165">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="c2788-166">`ShowDetails` Metody `ConvertibleCar` klasy nie jest wywoływana, niezależnie od tego, czy typ obiektu `ConvertibleCar`, jak w `TestCars1`, lub `Car`, jak w `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="c2788-166">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="c2788-167">Z drugiej strony `car3` wywołania `ShowDetails` metody z `Minivan` klasy w obu przypadkach, czy zawiera on typ `Minivan` lub typ `Car`.</span><span class="sxs-lookup"><span data-stu-id="c2788-167">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
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
  
 <span data-ttu-id="c2788-168">Metody `TestCars3` i `TestCars4` kompletny przykład.</span><span class="sxs-lookup"><span data-stu-id="c2788-168">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="c2788-169">Wywoływanie tych metod `ShowDetails` bezpośrednio, najpierw z obiektów zadeklarowany typ `ConvertibleCar` i `Minivan` (`TestCars3`), następnie z obiektami niezadeklarowanymi typ `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="c2788-169">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="c2788-170">Poniższy kod definiuje te dwie metody.</span><span class="sxs-lookup"><span data-stu-id="c2788-170">The following code defines these two methods.</span></span>  
  
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
  
 <span data-ttu-id="c2788-171">Metody generuje następujące dane wyjściowe, co odpowiada wyników z pierwszego przykładu w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="c2788-171">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
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
  
 <span data-ttu-id="c2788-172">Poniższy kod przedstawia kompletny projektu i jego danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c2788-172">The following code shows the complete project and its output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2788-173">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2788-173">See also</span></span>

- [<span data-ttu-id="c2788-174">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c2788-174">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c2788-175">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="c2788-175">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="c2788-176">Przechowywanie wersji przesłonięć i nowych słów kluczowych</span><span class="sxs-lookup"><span data-stu-id="c2788-176">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="c2788-177">base</span><span class="sxs-lookup"><span data-stu-id="c2788-177">base</span></span>](../../../csharp/language-reference/keywords/base.md)
- [<span data-ttu-id="c2788-178">abstract</span><span class="sxs-lookup"><span data-stu-id="c2788-178">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)
