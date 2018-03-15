---
title: "Tworzenie interfejsów ogólnych typu Variant (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 585d1fc3ee6114532d7ddbfd30f5e09950d3b0b0
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="c1aa3-102">Tworzenie interfejsów ogólnych typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="c1aa3-102">Creating Variant Generic Interfaces (C#)</span></span>
<span data-ttu-id="c1aa3-103">Można zadeklarować parametry typu ogólnego w interfejsach jako kowariantnego lub kontrawariantnego.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="c1aa3-104">*Kowariancja* umożliwia metod interfejsu do bardziej pochodnego zwracanych typów niż określone przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="c1aa3-105">*Kontrawariancja* umożliwia metod interfejsu do typy argumentu są mniej pochodnego od określonej przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="c1aa3-106">Ogólny interfejs, który ma kowariantnego lub kontrawariantnego parametry typu ogólnego jest nazywany *variant*.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1aa3-107">.NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="c1aa3-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="c1aa3-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="c1aa3-109">Deklarujący interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="c1aa3-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="c1aa3-110">Interfejsów ogólnych typu variant można zadeklarować przy użyciu `in` i `out` słowa kluczowe dla parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1aa3-111">`ref`, `in`, i `out` parametrów w języku C# nie może być wariantem.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="c1aa3-112">Typy wartości nie obsługują również wariancji.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="c1aa3-113">Można zadeklarować parametru typu ogólnego kowariantnego przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="c1aa3-114">Kowariantnego typu muszą spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="c1aa3-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="c1aa3-115">Typ jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="c1aa3-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` zadeklarowano kowariantny.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     <span data-ttu-id="c1aa3-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-117">There is one exception to this rule.</span></span> <span data-ttu-id="c1aa3-118">Jeśli masz to delegat generyczny kontrawariantnego jako parametr metody dla obiekt delegowany mogą używać typu co parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="c1aa3-119">Jest to zilustrowane przez typ `R` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="c1aa3-120">Aby uzyskać więcej informacji, zobacz [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [wariancji Func i akcji Delegaty ogólne (C#) przy użyciu](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="c1aa3-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   <span data-ttu-id="c1aa3-121">Typ nie jest używany jako ogólne ograniczenia dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="c1aa3-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-122">This is illustrated in the following code.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 <span data-ttu-id="c1aa3-123">Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="c1aa3-124">Typ kontrawariantnego może służyć jedynie jako typ argumenty metody, a nie typu zwracanego metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="c1aa3-125">Można także kontrawariantnego typu dla ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="c1aa3-126">Poniższy kod przedstawia sposób zadeklarować interfejsu kontrawariantnego i użyć ogólne ograniczenia dla jednej z metod.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 <span data-ttu-id="c1aa3-127">Istnieje również możliwość obsługuje zarówno Kowariancja i kontrawariancja w ten sam interfejs, ale dla różnych typów parametrów, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="c1aa3-128">Implementującej interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="c1aa3-128">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="c1aa3-129">Zaimplementowanie interfejsów ogólnych typu variant w klasach przy użyciu składni, która jest używana dla niezmiennej interfejsów.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="c1aa3-130">Poniższy przykład kodu pokazuje, jak do zaimplementowania w klasie rodzajowej kowariantnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
```csharp  
interface ICovariant<out R>  
{  
    R GetSomething();  
}  
class SampleImplementation<R> : ICovariant<R>  
{  
    public R GetSomething()  
    {  
        // Some code.  
        return default(R);  
    }  
}  
```  
  
 <span data-ttu-id="c1aa3-131">Klasy, które implementują interfejsów typu variant są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="c1aa3-132">Rozważmy na przykład następujący kod.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-132">For example, consider the following code.</span></span>  
  
```csharp  
// The interface is covariant.  
ICovariant<Button> ibutton = new SampleImplementation<Button>();  
ICovariant<Object> iobj = ibutton;  
  
// The class is invariant.  
SampleImplementation<Button> button = new SampleImplementation<Button>();  
// The following statement generates a compiler error  
// because classes are invariant.  
// SampleImplementation<Object> obj = button;  
```  
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="c1aa3-133">Rozszerzanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="c1aa3-133">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="c1aa3-134">Podczas rozszerzania typu variant interfejs ogólny, należy użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="c1aa3-135">Kompilator wariancję z interfejsu, który zostanie rozszerzone nie są rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="c1aa3-136">Na przykład należy wziąć pod uwagę następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-136">For example, consider the following interfaces.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 <span data-ttu-id="c1aa3-137">W `IInvariant<T>` interfejsu, parametru typu ogólnego `T` jest niezmienne, natomiast w `IExtCovariant<out T>` parametr typu jest kowariantny, mimo że oba interfejsy rozszerzenia tego samego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="c1aa3-138">Ta zasada dotyczy kontrawariantnego parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-138">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="c1aa3-139">Można utworzyć interfejs, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny i interfejsu, w której jest kontrawariantny Jeśli rozszerzenie interfejsu parametr typu ogólnego `T` jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="c1aa3-140">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-140">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 <span data-ttu-id="c1aa3-141">Jednak jeśli parametr typu ogólnego `T` jest zadeklarowana kowariantnego w jeden interfejs, nie można zadeklarować go kontrawariantnego w interfejsie rozszerzanie lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="c1aa3-142">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-142">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="c1aa3-143">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="c1aa3-143">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="c1aa3-144">Podczas implementowania interfejsów ogólnych typu variant wariancję czasami może prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="c1aa3-145">Należy unikać to.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-145">This should be avoided.</span></span>  
  
 <span data-ttu-id="c1aa3-146">Na przykład jawnie w przypadku zastosowania tego samego typu variant interfejsu ogólne z parametrami innego typu ogólnego w jedną klasę, można utworzyć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="c1aa3-147">Kompilator nie tworzy w tym przypadku błąd, ale nie określono implementacji interfejsu, który zostanie wybrany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="c1aa3-148">Może to prowadzić do subtelnych błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="c1aa3-149">Rozważmy poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-149">Consider the following code example.</span></span>  
  
```csharp  
// Simple class hierarchy.  
class Animal { }  
class Cat : Animal { }  
class Dog : Animal { }  
  
// This class introduces ambiguity  
// because IEnumerable<out T> is covariant.  
class Pets : IEnumerable<Cat>, IEnumerable<Dog>  
{  
    IEnumerator<Cat> IEnumerable<Cat>.GetEnumerator()  
    {  
        Console.WriteLine("Cat");  
        // Some code.  
        return null;  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        // Some code.  
        return null;  
    }  
  
    IEnumerator<Dog> IEnumerable<Dog>.GetEnumerator()  
    {  
        Console.WriteLine("Dog");  
        // Some code.  
        return null;  
    }  
}  
class Program  
{  
    public static void Test()  
    {  
        IEnumerable<Animal> pets = new Pets();  
        pets.GetEnumerator();  
    }  
}  
```  
  
 <span data-ttu-id="c1aa3-150">W tym przykładzie jest nieokreślony sposób `pets.GetEnumerator` metody wybierze między `Cat` i `Dog`.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="c1aa3-151">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c1aa3-151">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1aa3-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1aa3-152">See Also</span></span>  
 [<span data-ttu-id="c1aa3-153">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="c1aa3-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="c1aa3-154">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)</span><span class="sxs-lookup"><span data-stu-id="c1aa3-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
