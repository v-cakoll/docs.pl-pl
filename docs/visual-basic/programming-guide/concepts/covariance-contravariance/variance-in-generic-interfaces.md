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
# <a name="variance-in-generic-interfaces-visual-basic"></a>Wariancje w interfejsach (Visual Basic)
.NET framework 4 wprowadzono wariancji obsługę kilka istniejących interfejsów ogólnych. Obsługa wariancja umożliwia niejawną konwersję klas, które implementują te interfejsy. Następujące interfejsy są teraz wariant:  
  
- <xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)  
  
- <xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)  
  
- <xref:System.Linq.IQueryable%601> (T jest kowariantny)  
  
- <xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantne)  
  
- <xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)  
  
- <xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)  
  
- <xref:System.IComparable%601> (T jest kontrawariantny)  
  
 Kowariancja zezwala na metodę, aby mieć zwracanego typu bardziej pochodnego niż określone przez parametr typu ogólnego interfejsu. Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę te ogólne interfejsy: `IEnumerable(Of Object)` i `IEnumerable(Of String)`. `IEnumerable(Of String)` Interfejsu nie dziedziczy `IEnumerable(Of Object)` interfejsu. Jednak `String` typ dziedziczyć `Object` typu, a w niektórych przypadkach możesz chcieć przypisać obiekty te interfejsy do siebie nawzajem. Jest to pokazane w poniższym przykładzie kodu.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w Visual Basic z `Option Strict On`. Teraz możesz używać, ale `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.  
  
 Kontrawariancja umożliwia metodę, aby mieć typy argumentów, które są mniej pochodnego niż określona przez parametr ogólny interfejsu. Aby zilustrować kontrawariancja, załóżmy, że utworzono `BaseComparer` klasy do porównywania wystąpień `BaseClass` klasy. `BaseComparer` Klasy implementuje `IEqualityComparer(Of BaseClass)` interfejsu. Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest obecnie kontrawariantny, możesz użyć `BaseComparer` do porównywania wystąpień klas, które dziedziczą `BaseClass` klasy. Jest to pokazane w poniższym przykładzie kodu.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [przy użyciu wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Wariancje w interfejsach jest obsługiwana tylko dla typów odwołania. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable(Of Integer)` nie może być niejawnie konwertowane na `IEnumerable(Of Object)`, ponieważ liczby całkowite są reprezentowane przez typ wartości.  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 Jest również pamiętać, że klasy, które implementują interfejsów typu variant, są nadal niezmienne. Na przykład mimo że <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantne <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List(Of Object)` do `List(Of String)`. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Zobacz także

- [Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Tworzenie interfejsów typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Interfejsy ogólne](../../../../standard/generics/interfaces.md)
- [Wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
