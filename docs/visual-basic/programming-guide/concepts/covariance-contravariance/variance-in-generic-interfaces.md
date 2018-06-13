---
title: Wariancje w interfejsach (Visual Basic)
ms.date: 07/20/2015
ms.assetid: cf4096d0-4bb3-45a9-9a6b-f01e29a60333
ms.openlocfilehash: c18f014897ace71e437bd733ff6fcd1d4d8810dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643461"
---
# <a name="variance-in-generic-interfaces-visual-basic"></a>Wariancje w interfejsach (Visual Basic)
.NET framework 4 wprowadzono obsługę wariancji w kilku interfejsach istniejących. Obsługa wariancję umożliwia niejawna konwersja klas implementujących tych interfejsów. Następujące interfejsy są teraz wariant:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T jest kowariantny)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T jest kowariantny)  
  
-   <xref:System.Linq.IQueryable%601> (T jest kowariantny)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` i `TElement` są kowariantnego)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T jest kontrawariantny)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T jest kontrawariantny)  
  
-   <xref:System.IComparable%601> (T jest kontrawariantny)  
  
 Kowariancja zezwala na metodę typem zwracanym bardziej pochodny niż określone przez parametr typu ogólnego interfejsu. Aby zilustrować funkcji KOWARIANCJA, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable(Of Object)` i `IEnumerable(Of String)`. `IEnumerable(Of String)` Interfejsu nie dziedziczy `IEnumerable(Of Object)` interfejsu. Jednak `String` typ dziedziczy `Object` typu, a w niektórych przypadkach można przypisać obiekty te interfejsy do siebie. Przedstawiono to w poniższym przykładzie kodu.  
  
```vb  
Dim strings As IEnumerable(Of String) = New List(Of String)  
Dim objects As IEnumerable(Of Object) = strings  
```  
  
 We wcześniejszych wersjach programu .NET Framework, ten kod powoduje błąd kompilacji w języku Visual Basic z `Option Strict On`. Teraz można używać `strings` zamiast `objects`, jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejsu jest kowariantny.  
  
 Kontrawariancja zezwala na metodę typy argumentu są mniej pochodnego od określonej przez parametr ogólny interfejsu. Aby zilustrować kontrawariancji, załóżmy, że utworzono `BaseComparer` klasy do porównania wystąpienia `BaseClass` klasy. `BaseComparer` Klasa implementuje `IEqualityComparer(Of BaseClass)` interfejsu. Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest już kontrawariantnego, możesz użyć `BaseComparer` do porównania wystąpienia klas, które dziedziczą `BaseClass` klasy. Przedstawiono to w poniższym przykładzie kodu.  
  
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
  
 Aby uzyskać więcej przykładów, zobacz [korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Wariancje w interfejsach jest obsługiwana tylko dla typów odniesienia. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable(Of Integer)` nie można niejawnie przekonwertować `IEnumerable(Of Object)`, ponieważ liczb całkowitych są reprezentowane przez typ wartości.  
  
```vb  
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)  
' The following statement generates a compiler error  
' with Option Strict On, because Integer is a value type.  
' Dim objects As IEnumerable(Of Object) = integers  
```  
  
 Jest również pamiętać, że klas implementujących interfejsów typu variant są nadal niezmiennej. Na przykład chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs kowariantnego <xref:System.Collections.Generic.IEnumerable%601>, nie można niejawnie przekonwertować `List(Of Object)` do `List(Of String)`. Jest to zilustrowane w poniższym przykładzie kodu.  
  
```vb  
' The following statement generates a compiler error  
' because classes are invariant.  
' Dim list As List(Of Object) = New List(Of String)  
  
' You can use the interface object instead.  
Dim listObjects As IEnumerable(Of Object) = New List(Of String)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [Interfejsy ogólne](../../../../standard/generics/interfaces.md)  
 [Wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
