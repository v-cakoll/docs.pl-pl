---
title: Wariancje w interfejsach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: 50a1aeb5c17a0f193b9e90ca2167ef298f7ed237
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787221"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a><span data-ttu-id="ce2db-102">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2db-102">Variance in Generic Interfaces (Visual Basic)</span></span>
<span data-ttu-id="ce2db-103">.NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ce2db-103">.NET Framework 4 introduced variance support for several existing generic interfaces.</span></span> <span data-ttu-id="ce2db-104">Obsługa wariancja umożliwia niejawną konwersję klas, które implementują te interfejsy.</span><span class="sxs-lookup"><span data-stu-id="ce2db-104">Variance support enables implicit conversion of classes that implement these interfaces.</span></span> <span data-ttu-id="ce2db-105">Następujące interfejsy są teraz wariant:</span><span class="sxs-lookup"><span data-stu-id="ce2db-105">The following interfaces are now variant:</span></span>  
  
- <span data-ttu-id="ce2db-106"><xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-106"><xref:System.Collections.Generic.IEnumerable%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="ce2db-107"><xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-107"><xref:System.Collections.Generic.IEnumerator%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="ce2db-108"><xref:System.Linq.IQueryable%601> (T jest kowariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-108"><xref:System.Linq.IQueryable%601> (T is covariant)</span></span>  
  
- <span data-ttu-id="ce2db-109"><xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantne)</span><span class="sxs-lookup"><span data-stu-id="ce2db-109"><xref:System.Linq.IGrouping%602> (`TKey` and `TElement` are covariant)</span></span>  
  
- <span data-ttu-id="ce2db-110"><xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-110"><xref:System.Collections.Generic.IComparer%601> (T is contravariant)</span></span>  
  
- <span data-ttu-id="ce2db-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-111"><xref:System.Collections.Generic.IEqualityComparer%601> (T is contravariant)</span></span>  
  
- <span data-ttu-id="ce2db-112"><xref:System.IComparable%601> (T jest kontrawariantny)</span><span class="sxs-lookup"><span data-stu-id="ce2db-112"><xref:System.IComparable%601> (T is contravariant)</span></span>  
  
 <span data-ttu-id="ce2db-113">Kowariancja zezwala na metodę, aby mieć zwracanego typu bardziej pochodnego niż określone przez parametr typu ogólnego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-113">Covariance permits a method to have a more derived return type than that defined by the generic type parameter of the interface.</span></span> <span data-ttu-id="ce2db-114">Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę te ogólne interfejsy: `IEnumerable(Of Object)` i `IEnumerable(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="ce2db-114">To illustrate the covariance feature, consider these generic interfaces: `IEnumerable(Of Object)` and `IEnumerable(Of String)`.</span></span> <span data-ttu-id="ce2db-115">`IEnumerable(Of String)` Interfejsu nie dziedziczy `IEnumerable(Of Object)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-115">The `IEnumerable(Of String)` interface does not inherit the `IEnumerable(Of Object)` interface.</span></span> <span data-ttu-id="ce2db-116">Jednak `String` typ dziedziczyć `Object` typu, a w niektórych przypadkach możesz chcieć przypisać obiekty te interfejsy do siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="ce2db-116">However, the `String` type does inherit the `Object` type, and in some cases you may want to assign objects of these interfaces to each other.</span></span> <span data-ttu-id="ce2db-117">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-117">This is shown in the following code example.</span></span>  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 <span data-ttu-id="ce2db-118">We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w Visual Basic z `Option Strict On`.</span><span class="sxs-lookup"><span data-stu-id="ce2db-118">In earlier versions of the .NET Framework, this code causes a compilation error in Visual Basic with `Option Strict On`.</span></span> <span data-ttu-id="ce2db-119">Teraz możesz używać, ale `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="ce2db-119">But now you can use `strings` instead of `objects`, as shown in the previous example, because the <xref:System.Collections.Generic.IEnumerable%601> interface is covariant.</span></span>  
  
 <span data-ttu-id="ce2db-120">Kontrawariancja umożliwia metodę, aby mieć typy argumentów, które są mniej pochodnego niż określona przez parametr ogólny interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-120">Contravariance permits a method to have argument types that are less derived than that specified by the generic parameter of the interface.</span></span> <span data-ttu-id="ce2db-121">Aby zilustrować kontrawariancja, załóżmy, że utworzono `BaseComparer` klasy do porównywania wystąpień `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ce2db-121">To illustrate contravariance, assume that you have created a `BaseComparer` class to compare instances of the `BaseClass` class.</span></span> <span data-ttu-id="ce2db-122">`BaseComparer` Klasy implementuje `IEqualityComparer(Of BaseClass)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-122">The `BaseComparer` class implements the `IEqualityComparer(Of BaseClass)` interface.</span></span> <span data-ttu-id="ce2db-123">Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest obecnie kontrawariantny, możesz użyć `BaseComparer` do porównywania wystąpień klas, które dziedziczą `BaseClass` klasy.</span><span class="sxs-lookup"><span data-stu-id="ce2db-123">Because the <xref:System.Collections.Generic.IEqualityComparer%601> interface is now contravariant, you can use `BaseComparer` to compare instances of classes that inherit the `BaseClass` class.</span></span> <span data-ttu-id="ce2db-124">Jest to pokazane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-124">This is shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="ce2db-125">Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span><span class="sxs-lookup"><span data-stu-id="ce2db-125">For more examples, see [Using Variance in Interfaces for Generic Collections (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).</span></span>  
  
 <span data-ttu-id="ce2db-126">Wariancje w interfejsach jest obsługiwana tylko dla typów odwołania.</span><span class="sxs-lookup"><span data-stu-id="ce2db-126">Variance in generic interfaces is supported for reference types only.</span></span> <span data-ttu-id="ce2db-127">Typy wartości nie obsługują wariancji.</span><span class="sxs-lookup"><span data-stu-id="ce2db-127">Value types do not support variance.</span></span> <span data-ttu-id="ce2db-128">Na przykład `IEnumerable(Of Integer)` nie może być niejawnie konwertowane na `IEnumerable(Of Object)`, ponieważ liczby całkowite są reprezentowane przez typ wartości.</span><span class="sxs-lookup"><span data-stu-id="ce2db-128">For example, `IEnumerable(Of Integer)` cannot be implicitly converted to `IEnumerable(Of Object)`, because integers are represented by a value type.</span></span>  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 <span data-ttu-id="ce2db-129">Jest również pamiętać, że klasy, które implementują interfejsów typu variant, są nadal niezmienne.</span><span class="sxs-lookup"><span data-stu-id="ce2db-129">It is also important to remember that classes that implement variant interfaces are still invariant.</span></span> <span data-ttu-id="ce2db-130">Na przykład mimo że <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantne <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List(Of Object)` do `List(Of String)`.</span><span class="sxs-lookup"><span data-stu-id="ce2db-130">For example, although <xref:System.Collections.Generic.List%601> implements the covariant interface <xref:System.Collections.Generic.IEnumerable%601>, you cannot implicitly convert `List(Of Object)` to `List(Of String)`.</span></span> <span data-ttu-id="ce2db-131">Jest to zilustrowane w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="ce2db-131">This is illustrated in the following code example.</span></span>  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce2db-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce2db-132">See also</span></span>

- [<span data-ttu-id="ce2db-133">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2db-133">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [<span data-ttu-id="ce2db-134">Tworzenie interfejsów typu Variant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2db-134">Creating Variant Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [<span data-ttu-id="ce2db-135">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="ce2db-135">Generic Interfaces</span></span>](../../../../standard/generics/interfaces.md)
- [<span data-ttu-id="ce2db-136">Wariancje w Delegatach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce2db-136">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
