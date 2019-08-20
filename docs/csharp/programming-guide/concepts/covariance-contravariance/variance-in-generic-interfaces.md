---
title: Wariancja w interfejsachC#ogólnych ()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 12a8b58983256be0ca2b56ea6ed09e724e0814c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595164"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="47eba-102">Wariancja w interfejsachC#ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="47eba-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="47eba-103">.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="47eba-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="47eba-104">Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="47eba-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="47eba-105">Gwiazdki z .NET Framework 4, następujące interfejsy są wariantem:</span><span class="sxs-lookup"><span data-stu-id="47eba-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="47eba-106"><xref:System.Collections.Generic.IEnumerable%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="47eba-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="47eba-107"><xref:System.Collections.Generic.IEnumerator%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="47eba-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="47eba-108"><xref:System.Linq.IQueryable%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="47eba-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="47eba-109"><xref:System.Linq.IGrouping%602>(`TKey` i`TElement` są współwariantowe)</span><span class="sxs-lookup"><span data-stu-id="47eba-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="47eba-110"><xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="47eba-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="47eba-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="47eba-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="47eba-112"><xref:System.IComparable%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="47eba-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="47eba-113">Począwszy od .NET Framework 4,5, następujące interfejsy są wariantem:</span><span class="sxs-lookup"><span data-stu-id="47eba-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="47eba-114"><xref:System.Collections.Generic.IReadOnlyList%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="47eba-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="47eba-115"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="47eba-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="47eba-116">Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="47eba-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="47eba-117">Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne `IEnumerable<Object>` : `IEnumerable<String>`i.</span><span class="sxs-lookup"><span data-stu-id="47eba-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="47eba-118">`IEnumerable<String>` Interfejs nie`IEnumerable<Object>` dziedziczy interfejsu.</span><span class="sxs-lookup"><span data-stu-id="47eba-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="47eba-119">`String` Jednak Typ`Object` dziedziczy typ, a w niektórych przypadkach może być konieczne przypisanie obiektów do tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="47eba-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="47eba-120">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="47eba-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="47eba-121">We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w C# i, jeśli `Option Strict` znajduje się w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="47eba-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="47eba-122">Ale teraz można użyć `strings` `objects`zamiast, jak pokazano w <xref:System.Collections.Generic.IEnumerable%601> poprzednim przykładzie, ponieważ interfejs jest współwariantem.</span><span class="sxs-lookup"><span data-stu-id="47eba-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="47eba-123">Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="47eba-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="47eba-124">Aby zilustrować kontrawariancja, założono, że utworzono `BaseComparer` klasę, aby porównać wystąpienia `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="47eba-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="47eba-125">`BaseComparer` Klasa`IEqualityComparer<BaseClass>` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="47eba-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="47eba-126">Ponieważ interfejs jest teraz kontrawariantne, można go użyć `BaseComparer` do porównania wystąpień klas, które dziedziczą `BaseClass` klasę. <xref:System.Collections.Generic.IEqualityComparer%601></span><span class="sxs-lookup"><span data-stu-id="47eba-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="47eba-127">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="47eba-127">This is shown in the following code example.</span></span>

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

<span data-ttu-id="47eba-128">Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w interfejsach dlaC#kolekcji ogólnych ()](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="47eba-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="47eba-129">Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="47eba-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="47eba-130">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="47eba-130">Value types do not support variance.</span></span> <span data-ttu-id="47eba-131">Na przykład `IEnumerable<int>` nie można konwertować niejawnie na `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="47eba-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="47eba-132">Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="47eba-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="47eba-133">Na przykład, chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>współwariantu, nie można jawnie skonwertować `List<String>` do `List<Object>`.</span><span class="sxs-lookup"><span data-stu-id="47eba-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="47eba-134">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="47eba-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="47eba-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47eba-135">See also</span></span>

- [<span data-ttu-id="47eba-136">Korzystanie z wariancji w interfejsach dlaC#kolekcji ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="47eba-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="47eba-137">Tworzenie interfejsów ogólnych typu VariantC#()</span><span class="sxs-lookup"><span data-stu-id="47eba-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="47eba-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="47eba-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="47eba-139">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="47eba-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
