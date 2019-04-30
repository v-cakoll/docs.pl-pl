---
title: Wariancje w interfejsach (C#)
ms.date: 04/10/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 5874a39a57f85695bedc3d1ffa61adf19fcdbe37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702480"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="56fb3-102">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="56fb3-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="56fb3-103">.NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="56fb3-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="56fb3-104">Obsługa wariancja umożliwia niejawną konwersję klas, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="56fb3-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="56fb3-105">Rozpoczęcie przeczytania artykułu z .NET Framework 4, następujące interfejsy są wariant:</span><span class="sxs-lookup"><span data-stu-id="56fb3-105">Staring with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="56fb3-106"><xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="56fb3-107"><xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="56fb3-108"><xref:System.Linq.IQueryable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="56fb3-109"><xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantne)</span><span class="sxs-lookup"><span data-stu-id="56fb3-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="56fb3-110"><xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="56fb3-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="56fb3-112"><xref:System.IComparable%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="56fb3-113">Począwszy od programu .NET Framework 4.5, następujące interfejsy są wariant:</span><span class="sxs-lookup"><span data-stu-id="56fb3-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="56fb3-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is contravariant)</span></span>

- <span data-ttu-id="56fb3-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="56fb3-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is contravariant)</span></span>

<span data-ttu-id="56fb3-116">Kowariancja zezwala na metodę, aby mieć zwracanego typu bardziej pochodnego niż określone przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="56fb3-117">Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę te ogólne interfejsy: `IEnumerable<Object>` i `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="56fb3-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="56fb3-118">`IEnumerable<String>` Interfejsu nie dziedziczy `IEnumerable<Object>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="56fb3-119">Jednak `String` typ dziedziczyć `Object` typu, a w niektórych przypadkach możesz chcieć przypisać obiekty te interfejsy do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="56fb3-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="56fb3-120">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="56fb3-121">We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w C# i, jeśli `Option Strict` jest włączona, w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="56fb3-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="56fb3-122">Teraz możesz używać, ale `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="56fb3-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="56fb3-123">Kontrawariancja umożliwia metodę, aby mieć typy argumentów, które są mniej pochodnego niż określona przez parametr ogólny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="56fb3-124">Aby zilustrować kontrawariancja, załóżmy, że utworzono `BaseComparer` klasy do porównywania wystąpień `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="56fb3-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="56fb3-125">`BaseComparer` Klasy implementuje `IEqualityComparer<BaseClass>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="56fb3-126">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest obecnie kontrawariantny, możesz użyć `BaseComparer` do porównywania wystąpień klas, które dziedziczą `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="56fb3-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="56fb3-127">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="56fb3-128">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w interfejsach dla kolekcji ogólnych (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="56fb3-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="56fb3-129">Wariancje w interfejsach jest obsługiwana tylko dla typów odwołania.</span><span class="sxs-lookup"><span data-stu-id="56fb3-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="56fb3-130">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="56fb3-130">Value types do not support variance.</span></span> <span data-ttu-id="56fb3-131">Na przykład `IEnumerable<int>` nie może być niejawnie konwertowane na `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="56fb3-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="56fb3-132">Jest również pamiętać, że klasy, które implementują interfejsów typu variant, są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="56fb3-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="56fb3-133">Na przykład mimo że <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantne <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List<Object>` do `List<String>`.</span><span class="sxs-lookup"><span data-stu-id="56fb3-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<Object>` to `List<String>`.</span></span> <span data-ttu-id="56fb3-134">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="56fb3-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="56fb3-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56fb3-135">See also</span></span>

- [<span data-ttu-id="56fb3-136">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="56fb3-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="56fb3-137">Tworzenie interfejsów typu Variant (C#)</span><span class="sxs-lookup"><span data-stu-id="56fb3-137">Creating Variant Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="56fb3-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="56fb3-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="56fb3-139">Wariancje w Delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="56fb3-139">Variance in Delegates (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
