---
title: Wariancja w interfejsach ogólnych (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 2020ea54734724de775192a1a438413a73003d17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169665"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="37ebb-102">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="37ebb-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="37ebb-103">.NET Framework 4 wprowadzono obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="37ebb-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="37ebb-104">Obsługa wariancji umożliwia niejawną konwersję klas, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="37ebb-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span>

<span data-ttu-id="37ebb-105">Począwszy od .NET Framework 4, następujące interfejsy są wariantowe:</span><span class="sxs-lookup"><span data-stu-id="37ebb-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="37ebb-106"><xref:System.Collections.Generic.IEnumerable%601>(T jest kowariant)</span><span class="sxs-lookup"><span data-stu-id="37ebb-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="37ebb-107"><xref:System.Collections.Generic.IEnumerator%601>(T jest kowariant)</span><span class="sxs-lookup"><span data-stu-id="37ebb-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="37ebb-108"><xref:System.Linq.IQueryable%601>(T jest kowariant)</span><span class="sxs-lookup"><span data-stu-id="37ebb-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="37ebb-109"><xref:System.Linq.IGrouping%602>(`TKey` `TElement` i są kowariantne)</span><span class="sxs-lookup"><span data-stu-id="37ebb-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="37ebb-110"><xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="37ebb-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="37ebb-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="37ebb-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="37ebb-112"><xref:System.IComparable%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="37ebb-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="37ebb-113">Począwszy od .NET Framework 4.5, następujące interfejsy są wariantowe:</span><span class="sxs-lookup"><span data-stu-id="37ebb-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="37ebb-114"><xref:System.Collections.Generic.IReadOnlyList%601>(T jest kowariant)</span><span class="sxs-lookup"><span data-stu-id="37ebb-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="37ebb-115"><xref:System.Collections.Generic.IReadOnlyCollection%601>(T jest kowariant)</span><span class="sxs-lookup"><span data-stu-id="37ebb-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="37ebb-116">Kowariancja pozwala metody mieć bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="37ebb-117">Aby zilustrować funkcję kowariancji, należy `IEnumerable<Object>` wziąć `IEnumerable<String>`pod uwagę te interfejsy ogólne: i .</span><span class="sxs-lookup"><span data-stu-id="37ebb-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="37ebb-118">Interfejs `IEnumerable<String>` nie dziedziczy `IEnumerable<Object>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="37ebb-119">Jednak `String` typ dziedziczy `Object` typ, aw niektórych przypadkach można przypisać obiekty tych interfejsów do siebie.</span><span class="sxs-lookup"><span data-stu-id="37ebb-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="37ebb-120">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="37ebb-121">We wcześniejszych wersjach programu .NET Framework ten kod powoduje błąd `Option Strict` kompilacji w języku C# i, jeśli jest włączony, w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="37ebb-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="37ebb-122">Ale teraz można `strings` użyć `objects`zamiast , jak pokazano <xref:System.Collections.Generic.IEnumerable%601> w poprzednim przykładzie, ponieważ interfejs jest kowariant.</span><span class="sxs-lookup"><span data-stu-id="37ebb-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="37ebb-123">Contravariance pozwala metody mieć typy argumentów, które są mniej pochodne niż określone przez parametr ogólny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="37ebb-124">Aby zilustrować contravariance, załóżmy, że utworzono `BaseComparer` klasę, aby porównać wystąpienia `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="37ebb-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="37ebb-125">Klasa `BaseComparer` implementuje interfejs `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="37ebb-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="37ebb-126">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest teraz kontrawariantny, `BaseComparer` można porównać wystąpienia klas, `BaseClass` które dziedziczą klasę.</span><span class="sxs-lookup"><span data-stu-id="37ebb-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="37ebb-127">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="37ebb-128">Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="37ebb-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="37ebb-129">Odchylenie w interfejsach ogólnych jest obsługiwane tylko dla typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="37ebb-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="37ebb-130">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="37ebb-130">Value types do not support variance.</span></span> <span data-ttu-id="37ebb-131">Na przykład `IEnumerable<int>` nie można niejawnie przekonwertować na `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="37ebb-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="37ebb-132">Należy również pamiętać, że klasy implementują interfejsy wariantowe są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="37ebb-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="37ebb-133">Na przykład <xref:System.Collections.Generic.List%601> mimo implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>kowariantny , `List<String>` `List<Object>`nie można niejawnie konwertować do .</span><span class="sxs-lookup"><span data-stu-id="37ebb-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="37ebb-134">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="37ebb-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="37ebb-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37ebb-135">See also</span></span>

- [<span data-ttu-id="37ebb-136">Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="37ebb-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="37ebb-137">Tworzenie wariantowych interfejsów ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="37ebb-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="37ebb-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="37ebb-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="37ebb-139">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="37ebb-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
