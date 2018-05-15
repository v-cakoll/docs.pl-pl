---
title: Wariancje w interfejsach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: c18f014897ace71e437bd733ff6fcd1d4d8810dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="4ca3d-102">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="4ca3d-103">.NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="4ca3d-104">Obsługa wariancję umożliwia niejawna konwersja klas implementujących tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="4ca3d-105">Następujące interfejsy są teraz wariant:</span><span class="sxs-lookup"><span data-stu-id="4ca3d-105">The following interfaces are now variant:</span></span>  
  
-   <span data-ttu-id="4ca3d-106"><xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-107"><xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-108"><xref:System.Linq.IQueryable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-109"><xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantnego)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-110"><xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
-   <span data-ttu-id="4ca3d-112"><xref:System.IComparable%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="4ca3d-113">Kowariancja zezwala na metodę typem zwracanym bardziej pochodny niż określone przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="4ca3d-114">Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable(Of Object)` i `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="4ca3d-115">`IEnumerable(Of String)` Interfejsu nie dziedziczy `IEnumerable(Of Object)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="4ca3d-116">Jednak `String` typ dziedziczy `Object` typu, a w niektórych przypadkach można przypisać obiekty te interfejsy do siebie.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="4ca3d-117">Przedstawiono to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="4ca3d-118">We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w języku Visual Basic z `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="4ca3d-119">Teraz można używać `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="4ca3d-120">Kontrawariancja zezwala na metodę typy argumentu są mniej pochodnego od określonej przez parametr ogólny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="4ca3d-121">Aby zilustrować kontrawariancji, załóżmy, że utworzono `BaseComparer` klasy do porównania wystąpienia `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="4ca3d-122">`BaseComparer` Klasa implementuje `IEqualityComparer(Of BaseClass)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="4ca3d-123">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest już kontrawariantnego, możesz użyć `BaseComparer` do porównania wystąpienia klas, które dziedziczą `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="4ca3d-124">Przedstawiono to w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="4ca3d-125">Aby uzyskać więcej przykładów, zobacz [korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="4ca3d-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="4ca3d-126">Wariancje w interfejsach jest obsługiwana tylko dla typów odniesienia.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="4ca3d-127">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-127">Value types do not support variance.</span></span> <span data-ttu-id="4ca3d-128">Na przykład `IEnumerable(Of Integer)` nie można niejawnie przekonwertować `IEnumerable(Of Object)`, ponieważ liczb całkowitych są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="4ca3d-129">Jest również pamiętać, że klas implementujących interfejsów typu variant są nadal niezmiennej.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="4ca3d-130">Na przykład chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantnego <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List(Of Object)` do `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="4ca3d-131">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="4ca3d-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="4ca3d-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ca3d-132">See Also</span></span>  
 [<span data-ttu-id="4ca3d-133">Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [<span data-ttu-id="4ca3d-134">Tworzenie interfejsów ogólnych typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [<span data-ttu-id="4ca3d-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="4ca3d-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)  
 [<span data-ttu-id="4ca3d-136">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ca3d-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
