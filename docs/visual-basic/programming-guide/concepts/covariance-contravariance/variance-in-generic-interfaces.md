---
title: Wariancje w interfejsach
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: df28a9f24518f24d1be89acba726da7dfbbf9570
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375593"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="e7cc9-102">Wariancja w interfejsach ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-102">Variance in Generic Interfaces (Visual Basic)</span></span>

<span data-ttu-id="e7cc9-103">.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="e7cc9-104">Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="e7cc9-105">Następujące interfejsy są teraz wariantem:</span><span class="sxs-lookup"><span data-stu-id="e7cc9-105">The following interfaces are now variant:</span></span>

- <span data-ttu-id="e7cc9-106"><xref:System.Collections.Generic.IEnumerable%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>

- <span data-ttu-id="e7cc9-107"><xref:System.Collections.Generic.IEnumerator%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>

- <span data-ttu-id="e7cc9-108"><xref:System.Linq.IQueryable%601>(T jest współwariantem)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>

- <span data-ttu-id="e7cc9-109"><xref:System.Linq.IGrouping%602>( `TKey` i `TElement` są współwariantowe)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>

- <span data-ttu-id="e7cc9-110"><xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="e7cc9-111"><xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>

- <span data-ttu-id="e7cc9-112"><xref:System.IComparable%601>(T jest kontrawariantne)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-112"><xref:System.IComparable%601> (T is contravariant)</span></span>

<span data-ttu-id="e7cc9-113">Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="e7cc9-114">Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable(Of Object)` i `IEnumerable(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="e7cc9-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="e7cc9-115">`IEnumerable(Of String)`Interfejs nie dziedziczy `IEnumerable(Of Object)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="e7cc9-116">Jednak `String` Typ dziedziczy `Object` Typ, a w niektórych przypadkach może być konieczne przypisanie obiektów do tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="e7cc9-117">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-117">This is shown in the following code example.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="e7cc9-118">We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w Visual Basic z `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="e7cc9-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="e7cc9-119">Ale teraz można użyć `strings` zamiast `objects` , jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejs jest współwariantem.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>

<span data-ttu-id="e7cc9-120">Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="e7cc9-121">Aby zilustrować kontrawariancja, założono, że utworzono klasę, `BaseComparer` Aby porównać wystąpienia `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="e7cc9-122">Klasa `BaseComparer` implementuje interfejs `IEqualityComparer(Of BaseClass)`.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="e7cc9-123">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest teraz kontrawariantne, można `BaseComparer` go użyć do porównania wystąpień klas, które dziedziczą `BaseClass` klasę.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="e7cc9-124">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-124">This is shown in the following code example.</span></span>

```vb
' Simple hierarchy of classes.
Class BaseClass
End Class

Class DerivedClass
    Inherits BaseClass
End Class

' Comparer class.
Class BaseComparer
    Implements IEqualityComparer(Of BaseClass)

    Public Function Equals1(ByVal x As BaseClass,
                            ByVal y As BaseClass) As Boolean _
                            Implements IEqualityComparer(Of BaseClass).Equals
        Return (x.Equals(y))
    End Function

    Public Function GetHashCode1(ByVal obj As BaseClass) As Integer _
        Implements IEqualityComparer(Of BaseClass).GetHashCode
        Return obj.GetHashCode
    End Function
End Class
Sub Test()
    Dim baseComparer As IEqualityComparer(Of BaseClass) = New BaseComparer
    ' Implicit conversion of IEqualityComparer(Of BaseClass) to
    ' IEqualityComparer(Of DerivedClass).
    Dim childComparer As IEqualityComparer(Of DerivedClass) = baseComparer
End Sub
```

<span data-ttu-id="e7cc9-125">Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="e7cc9-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).</span></span>

<span data-ttu-id="e7cc9-126">Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="e7cc9-127">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-127">Value types do not support variance.</span></span> <span data-ttu-id="e7cc9-128">Na przykład `IEnumerable(Of Integer)` nie można konwertować niejawnie na `IEnumerable(Of Object)` , ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

<span data-ttu-id="e7cc9-129">Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="e7cc9-130">Na przykład, chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs współwariantu <xref:System.Collections.Generic.IEnumerable%601> , nie można jawnie skonwertować `List(Of Object)` do `List(Of String)` .</span><span class="sxs-lookup"><span data-stu-id="e7cc9-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="e7cc9-131">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="e7cc9-131">This is illustrated in the following code example.</span></span>

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a><span data-ttu-id="e7cc9-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7cc9-132">See also</span></span>

- [<span data-ttu-id="e7cc9-133">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="e7cc9-134">Tworzenie interfejsów ogólnych typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)
- [<span data-ttu-id="e7cc9-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="e7cc9-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="e7cc9-136">Wariancja w delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7cc9-136">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)
