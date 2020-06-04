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
# <a name="variance-in-generic-interfaces-visual-basic"></a>Wariancja w interfejsach ogólnych (Visual Basic)

.NET Framework 4 wprowadziła obsługę wariancji dla kilku istniejących interfejsów ogólnych. Obsługa wariancji umożliwia niejawną konwersję klas implementujących te interfejsy. Następujące interfejsy są teraz wariantem:

- <xref:System.Collections.Generic.IEnumerable%601>(T jest współwariantem)

- <xref:System.Collections.Generic.IEnumerator%601>(T jest współwariantem)

- <xref:System.Linq.IQueryable%601>(T jest współwariantem)

- <xref:System.Linq.IGrouping%602>( `TKey` i `TElement` są współwariantowe)

- <xref:System.Collections.Generic.IComparer%601>(T jest kontrawariantne)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T jest kontrawariantne)

- <xref:System.IComparable%601>(T jest kontrawariantne)

Kowariancja zezwala metodzie na bardziej pochodny typ zwracany niż zdefiniowany przez parametr typu ogólnego interfejsu. Aby zilustrować funkcję kowariancji, należy wziąć pod uwagę następujące interfejsy ogólne: `IEnumerable(Of Object)` i `IEnumerable(Of String)` . `IEnumerable(Of String)`Interfejs nie dziedziczy `IEnumerable(Of Object)` interfejsu. Jednak `String` Typ dziedziczy `Object` Typ, a w niektórych przypadkach może być konieczne przypisanie obiektów do tych interfejsów. Jest to pokazane w poniższym przykładzie kodu.

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

We wcześniejszych wersjach .NET Framework ten kod powoduje błąd kompilacji w Visual Basic z `Option Strict On` . Ale teraz można użyć `strings` zamiast `objects` , jak pokazano w poprzednim przykładzie, ponieważ <xref:System.Collections.Generic.IEnumerable%601> interfejs jest współwariantem.

Kontrawariancja umożliwia metodzie posiadanie typów argumentów, które są mniej pochodne niż określone przez parametr generyczny interfejsu. Aby zilustrować kontrawariancja, założono, że utworzono klasę, `BaseComparer` Aby porównać wystąpienia `BaseClass` klasy. Klasa `BaseComparer` implementuje interfejs `IEqualityComparer(Of BaseClass)`. Ponieważ <xref:System.Collections.Generic.IEqualityComparer%601> interfejs jest teraz kontrawariantne, można `BaseComparer` go użyć do porównania wystąpień klas, które dziedziczą `BaseClass` klasę. Jest to pokazane w poniższym przykładzie kodu.

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

Aby uzyskać więcej przykładów, zobacz [Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md).

Wariancja w interfejsach ogólnych jest obsługiwana tylko w przypadku typów referencyjnych. Typy wartości nie obsługują wariancji. Na przykład `IEnumerable(Of Integer)` nie można konwertować niejawnie na `IEnumerable(Of Object)` , ponieważ liczby całkowite są reprezentowane przez typ wartości.

```vb
Dim integers As IEnumerable(Of Integer) = New List(Of Integer)
' The following statement generates a compiler error
' with Option Strict On, because Integer is a value type.
' Dim objects As IEnumerable(Of Object) = integers
```

Należy również pamiętać, że klasy, które implementują interfejsy wariantów, są nadal niezmienne. Na przykład, chociaż <xref:System.Collections.Generic.List%601> implementuje interfejs współwariantu <xref:System.Collections.Generic.IEnumerable%601> , nie można jawnie skonwertować `List(Of Object)` do `List(Of String)` . Jest to zilustrowane w poniższym przykładzie kodu.

```vb
' The following statement generates a compiler error
' because classes are invariant.
' Dim list As List(Of Object) = New List(Of String)

' You can use the interface object instead.
Dim listObjects As IEnumerable(Of Object) = New List(Of String)
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)](using-variance-in-interfaces-for-generic-collections.md)
- [Tworzenie interfejsów ogólnych typu Variant (Visual Basic)](creating-variant-generic-interfaces.md)
- [Interfejsy ogólne](../../../../standard/generics/interfaces.md)
- [Wariancja w delegatach (Visual Basic)](variance-in-delegates.md)
