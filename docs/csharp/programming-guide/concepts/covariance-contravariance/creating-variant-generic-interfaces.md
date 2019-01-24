---
title: Tworzenie interfejsów typu Variant (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 5ae3b309282712e3441b53ea4cfc316be3ca92d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614683"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="b3a28-102">Tworzenie interfejsów typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-102">Creating Variant Generic Interfaces (C#)</span></span>
<span data-ttu-id="b3a28-103">Możesz deklarować parametry typu ogólnego w interfejsach jako kowariantny lub kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="b3a28-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="b3a28-104">*Kowariancja* umożliwia metod interfejsu do mają bardziej pochodne typy zwracane niż określone przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b3a28-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="b3a28-105">*Kontrawariancja* umożliwia metod interfejsu mieć typy argumentów, które są mniej pochodnego niż określona przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="b3a28-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="b3a28-106">Ogólny interfejs, który ma kowariantne i kontrawariantne parametry typu ogólnego jest nazywany *wariant*.</span><span class="sxs-lookup"><span data-stu-id="b3a28-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3a28-107">.NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="b3a28-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="b3a28-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="b3a28-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="b3a28-109">Deklarujący interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b3a28-109">Declaring Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b3a28-110">Można zadeklarować interfejsów ogólnych typu variant, za pomocą `in` i `out` słowa kluczowe dla parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="b3a28-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3a28-111">`ref`, `in`, i `out` parametrów w języku C# nie może być typ variant.</span><span class="sxs-lookup"><span data-stu-id="b3a28-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="b3a28-112">Typy wartości nie obsługują także wariancji.</span><span class="sxs-lookup"><span data-stu-id="b3a28-112">Value types also do not support variance.</span></span>  
  
 <span data-ttu-id="b3a28-113">Można zadeklarować parametru typu generycznego kowariantne przy użyciu `out` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b3a28-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="b3a28-114">Kowariantnego typu musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="b3a28-114">The covariant type must satisfy the following conditions:</span></span>  
  
-   <span data-ttu-id="b3a28-115">Typ jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="b3a28-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="b3a28-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako kowariantny.</span><span class="sxs-lookup"><span data-stu-id="b3a28-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        R GetSomething();  
        // The following statement generates a compiler error.  
        // void SetSometing(R sampleArg);  
  
    }  
    ```  
  
     <span data-ttu-id="b3a28-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="b3a28-117">There is one exception to this rule.</span></span> <span data-ttu-id="b3a28-118">Jeśli Delegat ogólny kontrawariantny, jako parametru metody, można użyć typu co parametr typu ogólnego, dla delegata.</span><span class="sxs-lookup"><span data-stu-id="b3a28-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="b3a28-119">Jest to zilustrowane przez typ `R` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b3a28-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="b3a28-120">Aby uzyskać więcej informacji, zobacz [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych (C#) Func i](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="b3a28-120">For more information, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        void DoSomething(Action<R> callback);  
    }  
    ```  
  
-   <span data-ttu-id="b3a28-121">Typ nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="b3a28-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3a28-122">This is illustrated in the following code.</span></span>  
  
    ```csharp  
    interface ICovariant<out R>  
    {  
        // The following statement generates a compiler error  
        // because you can use only contravariant or invariant types  
        // in generic contstraints.  
        // void DoSomething<T>() where T : R;  
    }  
    ```  
  
 <span data-ttu-id="b3a28-123">Można zadeklarować kontrawariantnego parametru typu ogólnego przy użyciu `in` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b3a28-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="b3a28-124">Typ kontrawariantne może służyć jedynie jako typów argumentów metody, a nie typu zwracanego metody interfejsu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="b3a28-125">Można także kontrawariantnego typu dla ograniczenia ogólne.</span><span class="sxs-lookup"><span data-stu-id="b3a28-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="b3a28-126">Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantnego i na użytek ograniczenie generyczne jednej z jego metod.</span><span class="sxs-lookup"><span data-stu-id="b3a28-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>  
  
```csharp  
interface IContravariant<in A>  
{  
    void SetSomething(A sampleArg);  
    void DoSomething<T>() where T : A;  
    // The following statement generates a compiler error.  
    // A GetSomething();              
}  
```  
  
 <span data-ttu-id="b3a28-127">Istnieje również możliwość obsługuje zarówno kowariancji i kontrawariancji w ten sam interfejs, ale dla parametrów innego typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>  
  
```csharp  
interface IVariant<out R, in A>  
{  
    R GetSomething();  
    void SetSomething(A sampleArg);  
    R GetSetSometings(A sampleArg);  
}  
```  
  
## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="b3a28-128">Implementowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b3a28-128">Implementing Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b3a28-129">Możesz zaimplementować interfejsów ogólnych typu variant klas przy użyciu składni, która jest używana niezmienna interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b3a28-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="b3a28-130">Poniższy przykład kodu pokazuje sposób implementacji kowariantne interfejsu w klasie ogólnej.</span><span class="sxs-lookup"><span data-stu-id="b3a28-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>  
  
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
  
 <span data-ttu-id="b3a28-131">Klasy, które implementują interfejsów typu variant są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="b3a28-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="b3a28-132">Rozważmy na przykład, poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="b3a28-132">For example, consider the following code.</span></span>  
  
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
  
## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="b3a28-133">Rozszerzanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="b3a28-133">Extending Variant Generic Interfaces</span></span>  
 <span data-ttu-id="b3a28-134">Podczas rozszerzania typu variant interfejs ogólny, trzeba użyć `in` i `out` słów kluczowych, aby jawnie określić, czy interfejsu pochodnego obsługuje wariancji.</span><span class="sxs-lookup"><span data-stu-id="b3a28-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="b3a28-135">Kompilator nie są rozpoznawane przez odchylenie od interfejsu, który jest rozszerzany.</span><span class="sxs-lookup"><span data-stu-id="b3a28-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="b3a28-136">Na przykład należy wziąć pod uwagę następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="b3a28-136">For example, consider the following interfaces.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IInvariant<T> : ICovariant<T> { }  
interface IExtCovariant<out T> : ICovariant<T> { }  
```  
  
 <span data-ttu-id="b3a28-137">W `IInvariant<T>` interfejsu, parametr typu ogólnego `T` jest niezmienny, natomiast w `IExtCovariant<out T>` parametr typu jest kowariantny, mimo że oba interfejsy rozszerzyć ten sam interfejs.</span><span class="sxs-lookup"><span data-stu-id="b3a28-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="b3a28-138">Ta sama zasada dotyczy kontrawariantne parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="b3a28-138">The same rule is applied to contravariant generic type parameters.</span></span>  
  
 <span data-ttu-id="b3a28-139">Można utworzyć interfejsu, który rozszerza interfejs gdzie parametr typu ogólnego `T` jest kowariantny interfejs, w której jest kontrawariantny w rozszerzanie interfejsu parametr typu ogólnego i `T` jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="b3a28-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="b3a28-140">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-140">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
interface IContravariant<in T> { }  
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }  
```  
  
 <span data-ttu-id="b3a28-141">Jednak jeśli parametr typu ogólnego `T` jest kowariantny zadeklarowana w ramach jednego interfejsu, nie można zadeklarować je kontrawariantnego w interfejsie rozszerzanie lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="b3a28-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="b3a28-142">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-142">This is illustrated in the following code example.</span></span>  
  
```csharp  
interface ICovariant<out T> { }  
// The following statement generates a compiler error.  
// interface ICoContraVariant<in T> : ICovariant<T> { }  
```  
  
### <a name="avoiding-ambiguity"></a><span data-ttu-id="b3a28-143">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="b3a28-143">Avoiding Ambiguity</span></span>  
 <span data-ttu-id="b3a28-144">Podczas implementowania interfejsów ogólnych typu variant wariancji czasami może prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="b3a28-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="b3a28-145">Należy ich unikać.</span><span class="sxs-lookup"><span data-stu-id="b3a28-145">This should be avoided.</span></span>  
  
 <span data-ttu-id="b3a28-146">Na przykład w przypadku zastosowania jawnie tego samego typu variant ogólny interfejs z parametrami typu rodzajowego różnych w jednej klasie, można utworzyć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="b3a28-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="b3a28-147">Kompilator generuje błąd w takiej sytuacji, ale nie zostanie określony, zostanie wybrany co do implementacji interfejsu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3a28-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="b3a28-148">Może to prowadzić do subtelnych błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3a28-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="b3a28-149">Rozważmy następujący przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-149">Consider the following code example.</span></span>  
  
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
  
 <span data-ttu-id="b3a28-150">W tym przykładzie jest nieokreślona sposób, w jaki `pets.GetEnumerator` metoda wybiera między `Cat` i `Dog`.</span><span class="sxs-lookup"><span data-stu-id="b3a28-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="b3a28-151">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3a28-151">This could cause problems in your code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a28-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3a28-152">See also</span></span>

- [<span data-ttu-id="b3a28-153">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-153">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="b3a28-154">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
