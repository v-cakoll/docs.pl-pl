---
title: Tworzenie interfejsów ogólnych typu Variant (C#)
ms.date: 07/20/2015
ms.assetid: 30330ec4-9df2-4838-a535-6c406d0ed4df
ms.openlocfilehash: 27760fd73c8c40fc108106b87b2102ab5e07263c
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241386"
---
# <a name="creating-variant-generic-interfaces-c"></a><span data-ttu-id="7d6dd-102">Tworzenie interfejsów ogólnych typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="7d6dd-102">Creating Variant Generic Interfaces (C#)</span></span>

<span data-ttu-id="7d6dd-103">Parametry typu ogólnego można zadeklarować w interfejsach jako współvariant lub kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-103">You can declare generic type parameters in interfaces as covariant or contravariant.</span></span> <span data-ttu-id="7d6dd-104">*Kowariancja* umożliwia metodom interfejsu posiadanie bardziej pochodnych typów zwracanych niż te zdefiniowane przez parametry typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-104">*Covariance* allows interface methods to have more derived return types than that defined by the generic type parameters.</span></span> <span data-ttu-id="7d6dd-105">*Kontrawariancja* umożliwia metodom interfejsu posiadanie typów argumentów, które są mniej pochodne niż określone przez parametry ogólne.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-105">*Contravariance* allows interface methods to have argument types that are less derived than that specified by the generic parameters.</span></span> <span data-ttu-id="7d6dd-106">Ogólny interfejs, który ma parametry typu generycznego lub kontrawariantne, nazywa się *wariantem*.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-106">A generic interface that has covariant or contravariant generic type parameters is called *variant*.</span></span>

> [!NOTE]
> <span data-ttu-id="7d6dd-107">.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-107">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="7d6dd-108">Aby zapoznać się z listą interfejsów wariantów w programie .NET, zobacz [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="7d6dd-108">For the list of the variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>

## <a name="declaring-variant-generic-interfaces"></a><span data-ttu-id="7d6dd-109">Deklarowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="7d6dd-109">Declaring Variant Generic Interfaces</span></span>

<span data-ttu-id="7d6dd-110">Można zadeklarować interfejsy ogólne wariantu przy użyciu `in` `out` słów kluczowych i dla parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-110">You can declare variant generic interfaces by using the `in` and `out` keywords for generic type parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d6dd-111">`ref``in`Parametry, i `out` w języku C# nie mogą być wariantem.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-111">`ref`, `in`, and `out` parameters in C# cannot be variant.</span></span> <span data-ttu-id="7d6dd-112">Typy wartości nie obsługują również wariancji.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-112">Value types also do not support variance.</span></span>

<span data-ttu-id="7d6dd-113">Za pomocą słowa kluczowego można zadeklarować współwariant parametru typu ogólnego `out` .</span><span class="sxs-lookup"><span data-stu-id="7d6dd-113">You can declare a generic type parameter covariant by using the `out` keyword.</span></span> <span data-ttu-id="7d6dd-114">Typ współwariantu musi spełniać następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="7d6dd-114">The covariant type must satisfy the following conditions:</span></span>

- <span data-ttu-id="7d6dd-115">Typ jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-115">The type is used only as a return type of interface methods and not used as a type of method arguments.</span></span> <span data-ttu-id="7d6dd-116">Jest to zilustrowane w poniższym przykładzie, w którym typ `R` jest zadeklarowany jako współvariant.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-116">This is illustrated in the following example, in which the type `R` is declared covariant.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        R GetSomething();
        // The following statement generates a compiler error.
        // void SetSomething(R sampleArg);

    }
    ```

    <span data-ttu-id="7d6dd-117">Istnieje jeden wyjątek dla tej reguły.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-117">There is one exception to this rule.</span></span> <span data-ttu-id="7d6dd-118">Jeśli masz delegata generycznego kontrawariantne jako parametr metody, możesz użyć typu jako parametru typu ogólnego dla delegata.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-118">If you have a contravariant generic delegate as a method parameter, you can use the type as a generic type parameter for the delegate.</span></span> <span data-ttu-id="7d6dd-119">Jest to zilustrowane przez typ `R` w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-119">This is illustrated by the type `R` in the following example.</span></span> <span data-ttu-id="7d6dd-120">Aby uzyskać więcej informacji, zobacz [Wariancja w delegatach (c#)](./variance-in-delegates.md) i [Korzystanie z wariancji dla delegatów funkcji Func i Action (c#)](./using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="7d6dd-120">For more information, see [Variance in Delegates (C#)](./variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates (C#)](./using-variance-for-func-and-action-generic-delegates.md).</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        void DoSomething(Action<R> callback);
    }
    ```

- <span data-ttu-id="7d6dd-121">Typ nie jest używany jako ograniczenie ogólne metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-121">The type is not used as a generic constraint for the interface methods.</span></span> <span data-ttu-id="7d6dd-122">Jest to zilustrowane w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-122">This is illustrated in the following code.</span></span>

    ```csharp
    interface ICovariant<out R>
    {
        // The following statement generates a compiler error
        // because you can use only contravariant or invariant types
        // in generic constraints.
        // void DoSomething<T>() where T : R;
    }
    ```

<span data-ttu-id="7d6dd-123">Parametry typu ogólnego kontrawariantne można zadeklarować za pomocą `in` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-123">You can declare a generic type parameter contravariant by using the `in` keyword.</span></span> <span data-ttu-id="7d6dd-124">Typ kontrawariantne może być używany tylko jako typ argumentów metody, a nie jako zwracany typ metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-124">The contravariant type can be used only as a type of method arguments and not as a return type of interface methods.</span></span> <span data-ttu-id="7d6dd-125">Typ kontrawariantne może być również używany dla ograniczeń ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-125">The contravariant type can also be used for generic constraints.</span></span> <span data-ttu-id="7d6dd-126">Poniższy kod przedstawia sposób deklarowania interfejsu kontrawariantne i używania ograniczenia ogólnego dla jednej z jej metod.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-126">The following code shows how to declare a contravariant interface and use a generic constraint for one of its methods.</span></span>

```csharp
interface IContravariant<in A>
{
    void SetSomething(A sampleArg);
    void DoSomething<T>() where T : A;
    // The following statement generates a compiler error.
    // A GetSomething();
}
```

<span data-ttu-id="7d6dd-127">Istnieje również możliwość obsługi zarówno kowariancji, jak i kontrawariancja w tym samym interfejsie, ale dla różnych parametrów typu, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-127">It is also possible to support both covariance and contravariance in the same interface, but for different type parameters, as shown in the following code example.</span></span>

```csharp
interface IVariant<out R, in A>
{
    R GetSomething();
    void SetSomething(A sampleArg);
    R GetSetSomethings(A sampleArg);
}
```

## <a name="implementing-variant-generic-interfaces"></a><span data-ttu-id="7d6dd-128">Implementowanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="7d6dd-128">Implementing Variant Generic Interfaces</span></span>

<span data-ttu-id="7d6dd-129">W klasach można zaimplementować interfejsy ogólne o zmiennej, korzystając z tej samej składni, która jest używana dla interfejsów niezmienna.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-129">You implement variant generic interfaces in classes by using the same syntax that is used for invariant interfaces.</span></span> <span data-ttu-id="7d6dd-130">Poniższy przykład kodu pokazuje, jak zaimplementować interfejs współvariant w klasie generycznej.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-130">The following code example shows how to implement a covariant interface in a generic class.</span></span>

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

<span data-ttu-id="7d6dd-131">Klasy implementujące interfejsy Variant są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-131">Classes that implement variant interfaces are invariant.</span></span> <span data-ttu-id="7d6dd-132">Rozważmy na przykład poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-132">For example, consider the following code.</span></span>

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

## <a name="extending-variant-generic-interfaces"></a><span data-ttu-id="7d6dd-133">Rozszerzanie interfejsów ogólnych typu Variant</span><span class="sxs-lookup"><span data-stu-id="7d6dd-133">Extending Variant Generic Interfaces</span></span>

<span data-ttu-id="7d6dd-134">Po rozłączeniu uniwersalnego interfejsu wariantowego należy użyć `in` `out` słów kluczowych i, aby jawnie określić, czy interfejs pochodny obsługuje wariancję.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-134">When you extend a variant generic interface, you have to use the `in` and `out` keywords to explicitly specify whether the derived interface supports variance.</span></span> <span data-ttu-id="7d6dd-135">Kompilator nie wywnioskuje wariancji z rozszerzanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-135">The compiler does not infer the variance from the interface that is being extended.</span></span> <span data-ttu-id="7d6dd-136">Rozważmy na przykład następujące interfejsy.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-136">For example, consider the following interfaces.</span></span>

```csharp
interface ICovariant<out T> { }
interface IInvariant<T> : ICovariant<T> { }
interface IExtCovariant<out T> : ICovariant<T> { }
```

<span data-ttu-id="7d6dd-137">W `IInvariant<T>` interfejsie parametr typu generycznego `T` jest niezmienny, natomiast w `IExtCovariant<out T>` parametrze typu jest współwariant, chociaż oba interfejsy rozszerzającą ten sam interfejs.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-137">In the `IInvariant<T>` interface, the generic type parameter `T` is invariant, whereas in `IExtCovariant<out T>` the type parameter is covariant, although both interfaces extend the same interface.</span></span> <span data-ttu-id="7d6dd-138">Ta sama reguła jest stosowana do parametrów typu ogólnego kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-138">The same rule is applied to contravariant generic type parameters.</span></span>

<span data-ttu-id="7d6dd-139">Można utworzyć interfejs, który rozszerza zarówno interfejs, w którym parametr typu generycznego `T` to współwariant, jak i interfejs, w którym jest kontrawariantne, jeśli w rozszerzanym interfejsie parametr typu generycznego `T` jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-139">You can create an interface that extends both the interface where the generic type parameter `T` is covariant and the interface where it is contravariant if in the extending interface the generic type parameter `T` is invariant.</span></span> <span data-ttu-id="7d6dd-140">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-140">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
interface IContravariant<in T> { }
interface IInvariant<T> : ICovariant<T>, IContravariant<T> { }
```

<span data-ttu-id="7d6dd-141">Jeśli jednak parametr typu generycznego `T` jest zadeklarowany jako współwariant w jednym interfejsie, nie można zadeklarować go kontrawariantne w interfejsie rozszerzającym lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-141">However, if a generic type parameter `T` is declared covariant in one interface, you cannot declare it contravariant in the extending interface, or vice versa.</span></span> <span data-ttu-id="7d6dd-142">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-142">This is illustrated in the following code example.</span></span>

```csharp
interface ICovariant<out T> { }
// The following statement generates a compiler error.
// interface ICoContraVariant<in T> : ICovariant<T> { }
```

### <a name="avoiding-ambiguity"></a><span data-ttu-id="7d6dd-143">Unikanie niejednoznaczności</span><span class="sxs-lookup"><span data-stu-id="7d6dd-143">Avoiding Ambiguity</span></span>

<span data-ttu-id="7d6dd-144">Podczas implementowania interfejsów ogólnych typu Variant WARIANCJA może czasami prowadzić do niejednoznaczności.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-144">When you implement variant generic interfaces, variance can sometimes lead to ambiguity.</span></span> <span data-ttu-id="7d6dd-145">Należy to uniknąć.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-145">This should be avoided.</span></span>

<span data-ttu-id="7d6dd-146">Na przykład w przypadku jawnego zaimplementowania tego samego uniwersalnego interfejsu wariantu z różnymi parametrami typu ogólnego w jednej klasie można utworzyć niejednoznaczność.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-146">For example, if you explicitly implement the same variant generic interface with different generic type parameters in one class, it can create ambiguity.</span></span> <span data-ttu-id="7d6dd-147">Kompilator nie generuje błędu w tym przypadku, ale nie jest określony, która implementacja interfejsu zostanie wybrana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-147">The compiler does not produce an error in this case, but it is not specified which interface implementation will be chosen at runtime.</span></span> <span data-ttu-id="7d6dd-148">Może to prowadzić do delikatnych usterek w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-148">This could lead to subtle bugs in your code.</span></span> <span data-ttu-id="7d6dd-149">Spójrz na poniższy przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-149">Consider the following code example.</span></span>

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

<span data-ttu-id="7d6dd-150">W tym przykładzie nie określono `pets.GetEnumerator` metody wybieranej między `Cat` i `Dog` .</span><span class="sxs-lookup"><span data-stu-id="7d6dd-150">In this example, it is unspecified how the `pets.GetEnumerator` method chooses between `Cat` and `Dog`.</span></span> <span data-ttu-id="7d6dd-151">Może to spowodować problemy w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7d6dd-151">This could cause problems in your code.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d6dd-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d6dd-152">See also</span></span>

- [<span data-ttu-id="7d6dd-153">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="7d6dd-153">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
- [<span data-ttu-id="7d6dd-154">Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)</span><span class="sxs-lookup"><span data-stu-id="7d6dd-154">Using Variance for Func and Action Generic Delegates (C#)</span></span>](./using-variance-for-func-and-action-generic-delegates.md)
