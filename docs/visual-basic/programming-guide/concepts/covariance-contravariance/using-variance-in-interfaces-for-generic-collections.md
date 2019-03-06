---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 3c7cde2baf6d8b163c6765b87d6bebef803eb6ee
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356705"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)

Kowariantne interfejs umożliwia jego metod zwrócić więcej typów pochodnych niż określone w interfejsie. Interfejs kontrawariantnego umożliwia jego metod akceptował parametry typu mniej pochodnego niż warunki określone w interfejsie.

W programie .NET Framework 4, kilka istniejące interfejsy stało się kowariantne i kontrawariantne. Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601>. Dzięki temu można ponownie użyć metody, które pracują z kolekcji ogólnych typów podstawowych dla kolekcji typów pochodnych.

Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).

## <a name="converting-generic-collections"></a>Konwertowanie kolekcji ogólnych

W poniższym przykładzie pokazano zalety obsługi Kowariancja w <xref:System.Collections.Generic.IEnumerable%601> interfejsu. `PrintFullName` Metoda przyjmuje zbiór `IEnumerable(Of Person)` typu jako parametru. Jednak można użyć ponownie go kolekcji `IEnumerable(Of Person)` typu, ponieważ `Employee` dziedziczy `Person`.

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class

' The method has a parameter of the IEnumerable(Of Person) type.
Public Sub PrintFullName(ByVal persons As IEnumerable(Of Person))
    For Each person As Person In persons
        Console.WriteLine(
            "Name: " & person.FirstName & " " & person.LastName)
    Next
End Sub

Sub Main()
    Dim employees As IEnumerable(Of Employee) = New List(Of Employee)

    ' You can pass IEnumerable(Of Employee),
    ' although the method expects IEnumerable(Of Person).

    PrintFullName(employees)

End Sub
```

## <a name="comparing-generic-collections"></a>Porównywanie kolekcji ogólnych

W poniższym przykładzie pokazano zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsu. `PersonComparer` Klasy implementuje `IComparer(Of Person)` interfejsu. Jednakże, można ponownie użyć tej klasy, aby porównać sekwencję obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person`.

```vb
' Simple hierarchy of classes.
Public Class Person
    Public Property FirstName As String
    Public Property LastName As String
End Class

Public Class Employee
    Inherits Person
End Class
' The custom comparer for the Person type
' with standard implementations of Equals()
' and GetHashCode() methods.
Class PersonComparer
    Implements IEqualityComparer(Of Person)

    Public Function Equals1(
        ByVal x As Person,
        ByVal y As Person) As Boolean _
        Implements IEqualityComparer(Of Person).Equals

        If x Is y Then Return True
        If x Is Nothing OrElse y Is Nothing Then Return False
        Return (x.FirstName = y.FirstName) AndAlso
            (x.LastName = y.LastName)
    End Function
    Public Function GetHashCode1(
        ByVal person As Person) As Integer _
        Implements IEqualityComparer(Of Person).GetHashCode

        If person Is Nothing Then Return 0
        Dim hashFirstName =
            If(person.FirstName Is Nothing,
            0, person.FirstName.GetHashCode())
        Dim hashLastName = person.LastName.GetHashCode()
        Return hashFirstName Xor hashLastName
    End Function
End Class

Sub Main()
    Dim employees = New List(Of Employee) From {
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}
    }

    ' You can pass PersonComparer,
    ' which implements IEqualityComparer(Of Person),
    ' although the method expects IEqualityComparer(Of Employee)

    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())

    For Each employee In noduplicates
        Console.WriteLine(employee.FirstName & " " & employee.LastName)
    Next
End Sub
```

## <a name="see-also"></a>Zobacz także

- [Wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
