---
title: Wariancja w interfejsachC#ogólnych ()
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179061"
---
# <a name="variance-in-generic-interfaces-c"></a><span data-ttu-id="02788-102">Wariancja w interfejsachC#ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="02788-102">Variance in Generic Interfaces (C#)</span></span>

<span data-ttu-id="02788-103">.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="02788-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="02788-104">Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="02788-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> 

<span data-ttu-id="02788-105">Począwszy od .NET Framework 4, następujące interfejsy są wariantem:</span><span class="sxs-lookup"><span data-stu-id="02788-105">Starting with .NET Framework 4, the following interfaces are variant:</span></span>

- <span data-ttu-id="02788-106"><xref:System.Collections.Generic.IEnumerable%601> (T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="02788-107"><xref:System.Collections.Generic.IEnumerator%601> (T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="02788-108"><xref:System.Linq.IQueryable%601> (T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="02788-109"><xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="02788-110"><xref:System.Collections.Generic.IComparer%601> (T to kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="02788-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="02788-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T to kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="02788-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="02788-112"><xref:System.IComparable%601> (T to kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="02788-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="02788-113">Począwszy od .NET Framework 4,5, następujące interfejsy są wariantem:</span><span class="sxs-lookup"><span data-stu-id="02788-113">Starting with .NET Framework 4.5, the following interfaces are variant:</span></span>

- <span data-ttu-id="02788-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-114"><xref:System.Collections.Generic.IReadOnlyList%601> (T is covariant)</span></span>

- <span data-ttu-id="02788-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="02788-115"><xref:System.Collections.Generic.IReadOnlyCollection%601> (T is covariant)</span></span>

<span data-ttu-id="02788-116">Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="02788-116">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="02788-117">Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable<Object>` i `IEnumerable<String>`.</span><span class="sxs-lookup"><span data-stu-id="02788-117">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable<Object>` and `IEnumerable<String>`.</span></span> <span data-ttu-id="02788-118">Interfejs `IEnumerable<String>` nie dziedziczy interfejsu `IEnumerable<Object>`.</span><span class="sxs-lookup"><span data-stu-id="02788-118">The `IEnumerable<String>` interface does not inherit the `IEnumerable<Object>` interface.</span></span> <span data-ttu-id="02788-119">Jednak typ `String` dziedziczy typ `Object`, a w niektórych przypadkach może być konieczne przypisanie obiektów do obu tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="02788-119">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="02788-120">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="02788-120">This is shown in the following code example.</span></span>

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

<span data-ttu-id="02788-121">We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w C# i, jeśli `Option Strict` jest włączona, w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="02788-121">In earlier versions of the .NET Framework, this code causes a compilation error in C# and, if `Option Strict` is on, in Visual Basic.</span></span> <span data-ttu-id="02788-122">Teraz można użyć `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ interfejs <xref:System.Collections.Generic.IEnumerable%601> jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="02788-122">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="02788-123">Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="02788-123">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="02788-124">Aby zilustrować kontrawariancja, założono, że utworzono klasę `BaseComparer` w celu porównania wystąpień klasy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="02788-124">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="02788-125">Klasa `BaseComparer` implementuje interfejs `IEqualityComparer<BaseClass>`.</span><span class="sxs-lookup"><span data-stu-id="02788-125">The `BaseComparer` class implements the `IEqualityComparer<BaseClass>` interface.</span></span> <span data-ttu-id="02788-126">Ponieważ interfejs <xref:System.Collections.Generic.IEqualityComparer%601> jest teraz kontrawariantne, można użyć `BaseComparer` do porównania wystąpień klas, które dziedziczą klasę `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="02788-126">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="02788-127">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="02788-127">This is shown in the following code example.</span></span>

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

<span data-ttu-id="02788-128">Aby uzyskać więcej przykładów, zobacz [Używanie wariancji w interfejsach dlaC#kolekcji ogólnych ()](./using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="02788-128">For more examples, see [Using Variance in Interfaces for Generic Collections (C#)](./using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="02788-129">Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="02788-129">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="02788-130">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="02788-130">Value types do not support variance.</span></span> <span data-ttu-id="02788-131">Na przykład `IEnumerable<int>` nie może być niejawnie konwertowany do `IEnumerable<object>`, ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="02788-131">For example, `IEnumerable<int>` cannot be implicitly converted to `IEnumerable<object>`, because integers are represented by a value type.</span></span>

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

<span data-ttu-id="02788-132">Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="02788-132">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="02788-133">Na przykład mimo że <xref:System.Collections.Generic.List%601> implementuje interfejs współwariantowy <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie skonwertować `List<String>` na `List<Object>`.</span><span class="sxs-lookup"><span data-stu-id="02788-133">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List<String>` to `List<Object>`.</span></span> <span data-ttu-id="02788-134">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="02788-134">This is illustrated in the following code example.</span></span>

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a><span data-ttu-id="02788-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02788-135">See also</span></span>

- [<span data-ttu-id="02788-136">Korzystanie z wariancji w interfejsach dlaC#kolekcji ogólnych ()</span><span class="sxs-lookup"><span data-stu-id="02788-136">Using Variance in Interfaces for Generic Collections (C#)</span></span>](./using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="02788-137">Tworzenie interfejsów ogólnych typu VariantC#()</span><span class="sxs-lookup"><span data-stu-id="02788-137">Creating Variant Generic Interfaces (C#)</span></span>](./creating-variant-generic-interfaces.md)
- [<span data-ttu-id="02788-138">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="02788-138">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="02788-139">Wariancja w delegatach (C#)</span><span class="sxs-lookup"><span data-stu-id="02788-139">Variance in Delegates (C#)</span></span>](./variance-in-delegates.md)
