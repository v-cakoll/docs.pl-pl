---
title: Tworzenie wariantowych interfejsów ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 4ba72f28cd2ddd800f169387cc2c742159d4cb1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595310"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="1a690-102">Tworzenie wariantowych interfejsów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="1a690-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="1a690-103">Można zadeklarować ogólne parametry typu w interfejsach jako kowariantne lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="1a690-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="1a690-104">*Kowariancja* umożliwia metody interfejsu mają więcej pochodnych typów zwracanych niż zdefiniowane przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1a690-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="1a690-105">*Contravariance* umożliwia metody interfejsu mają typy argumentów, które są mniej pochodne niż określone przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="1a690-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="1a690-106">Ogólny interfejs, który ma kowariantne lub kontrawariantne parametry typu ogólnego, jest nazywany *wariantem*.</span><span class="sxs-lookup"><span data-stu-id="1a690-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="1a690-107">.NET Framework 4 wprowadzono obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1a690-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="1a690-108">Aby uzyskać listę interfejsów wariantów w platformie .NET Framework, zobacz [Wariancja w interfejsach ogólnych (C#).](./variance-in-generic-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="1a690-108">For the list of the variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="1a690-109">Deklarowanie wariantowych interfejsów ogólnych</span><span class="sxs-lookup"><span data-stu-id="1a690-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="1a690-110">Można zadeklarować wariant ogólnych `in` interfejsów przy użyciu i `out` słów kluczowych dla parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1a690-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1a690-111">`ref`, `in`a `out` parametry w języku C# nie mogą być wariantowe.</span><span class="sxs-lookup"><span data-stu-id="1a690-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="1a690-112">Typy wartości również nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="1a690-112">Value types also do not support variance.</span></span>

<span data-ttu-id="1a690-113">Można zadeklarować covariant parametru typu `out` ogólnego przy użyciu słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="1a690-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="1a690-114">Typ kowariantny musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="1a690-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="1a690-115">Typ jest używany tylko jako zwracany typ metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="1a690-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="1a690-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany covariant.</span><span class="sxs-lookup"><span data-stu-id="1a690-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="1a690-117">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="1a690-117">There is one exception to this rule.</span></span> <span data-ttu-id="1a690-118">Jeśli jako parametr metody masz kontrataki ogólny, możesz użyć tego typu jako parametru typu ogólnego dla pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="1a690-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="1a690-119">Jest to zilustrowane `R` przez typ w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1a690-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="1a690-120">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md) i [Korzystanie z wariancji dla func i akcji ogólnych delegatów (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="1a690-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="1a690-121">Typ nie jest używany jako ogólne ograniczenie dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a690-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="1a690-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a690-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="1a690-123">Można zadeklarować kontrawarianty parametru typu `in` ogólnego za pomocą słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="1a690-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="1a690-124">Typ kontrawariantny może służyć tylko jako typ argumentów metody, a nie jako zwracany typ metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a690-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="1a690-125">Typ kontrawariantny może być również używany dla ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1a690-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="1a690-126">Poniższy kod pokazuje, jak zadeklarować interfejs kontrawariantny i użyć ograniczenia ogólnego dla jednej z jego metod.</span><span class="sxs-lookup"><span data-stu-id="1a690-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="1a690-127">Możliwe jest również obsługa zarówno kowariancji, jak i kontrawaracji w tym samym interfejsie, ale dla różnych parametrów typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1a690-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="1a690-128">Implementowanie wariantowych interfejsów ogólnych</span><span class="sxs-lookup"><span data-stu-id="1a690-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="1a690-129">Implementowanie wariantu interfejsów ogólnych w klasach przy użyciu tej samej składni, która jest używana dla interfejsów niezmiennych.</span><span class="sxs-lookup"><span data-stu-id="1a690-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="1a690-130">W poniższym przykładzie kodu pokazano, jak zaimplementować interfejs kowariantny w klasie ogólnej.</span><span class="sxs-lookup"><span data-stu-id="1a690-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="1a690-131">Klasy implementują interfejsy wariantowe są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="1a690-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="1a690-132">Rozważmy na przykład następujący kod.</span><span class="sxs-lookup"><span data-stu-id="1a690-132">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="1a690-133">Rozszerzanie wariantowych interfejsów ogólnych</span><span class="sxs-lookup"><span data-stu-id="1a690-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="1a690-134">Po rozszerzeniu wariantu ogólny interfejs, `in` należy `out` użyć i słowa kluczowe jawnie określić, czy interfejs pochodny obsługuje wariancji.</span><span class="sxs-lookup"><span data-stu-id="1a690-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="1a690-135">Kompilator nie wywnioskować wariancji z interfejsu, który jest rozszerzony.</span><span class="sxs-lookup"><span data-stu-id="1a690-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="1a690-136">Rozważmy na przykład następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="1a690-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="1a690-137">W `IInvariant<T>` interfejsie parametr `T` typu ogólnego jest niezmienny, podczas gdy w `IExtCovariant<out T>` parametrze typu jest kowariantny, chociaż oba interfejsy rozszerzają ten sam interfejs.</span><span class="sxs-lookup"><span data-stu-id="1a690-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="1a690-138">Ta sama reguła jest stosowana do przeciwwariantnych parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="1a690-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="1a690-139">Można utworzyć interfejs, który rozszerza zarówno interfejs, `T` w którym parametr typu ogólnego jest kowariantny, jak i `T` interfejs, w którym jest kontrawariantny, jeśli w interfejsie rozszerzającym parametr typu ogólnego jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="1a690-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="1a690-140">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1a690-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="1a690-141">Jednak jeśli parametr `T` typu ogólnego jest zadeklarowany covariant w jednym interfejsie, nie można zadeklarować, że jest to kontrawarianty w interfejsie rozszerzającym lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="1a690-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="1a690-142">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="1a690-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="1a690-143">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="1a690-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="1a690-144">Podczas implementowania wariantu interfejsów ogólnych wariancja może czasami prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1a690-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="1a690-145">Należy tego unikać.</span><span class="sxs-lookup"><span data-stu-id="1a690-145">This should be avoided.</span></span>

<span data-ttu-id="1a690-146">Na przykład jeśli jawnie zaimplementujesz ten sam wariant ogólny interfejs z różnymi parametrami typu ogólnego w jednej klasie, można utworzyć niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="1a690-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="1a690-147">Kompilator nie generuje błąd w tym przypadku, ale nie określono, która implementacja interfejsu zostanie wybrana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1a690-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="1a690-148">Może to prowadzić do subtelnych błędów w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a690-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="1a690-149">Spójrz na poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="1a690-149">Consider the following code example.</span></span>

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

<span data-ttu-id="1a690-150">W tym przykładzie nie określono, `pets.GetEnumerator` w jaki `Cat` sposób `Dog`metoda wybiera między i .</span><span class="sxs-lookup"><span data-stu-id="1a690-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="1a690-151">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1a690-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a690-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a690-152">See also</span></span>

- [<span data-ttu-id="1a690-153">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="1a690-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="1a690-154">Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)</span><span class="sxs-lookup"><span data-stu-id="1a690-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
