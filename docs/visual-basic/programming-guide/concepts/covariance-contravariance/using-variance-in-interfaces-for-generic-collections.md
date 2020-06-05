---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: b762ce42215f9b24371313446637e95962677bfb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375644"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a>Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)

Interfejs współdzielny umożliwia metodom Zwracanie większej liczby typów pochodnych niż określone w interfejsie. Interfejs kontrawariantne umożliwia jej metodom akceptowanie parametrów o mniejszych typach pochodnych niż określone w interfejsie.

W .NET Framework 4, kilka istniejących interfejsów stał się współwariantem i kontrawariantne. Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> . Dzięki temu można ponownie użyć metod, które działają z ogólnymi kolekcjami typów podstawowych dla kolekcji typów pochodnych.

Aby uzyskać listę interfejsów wariantów w .NET Framework, zobacz [Wariancja w interfejsach ogólnych (Visual Basic)](variance-in-generic-interfaces.md).

## <a name="converting-generic-collections"></a>Konwertowanie kolekcji ogólnych

Poniższy przykład ilustruje zalety obsługi kowariancji w <xref:System.Collections.Generic.IEnumerable%601> interfejsie. `PrintFullName`Metoda akceptuje kolekcję `IEnumerable(Of Person)` typu jako parametr. Można jednak ponownie użyć go dla kolekcji `IEnumerable(Of Person)` typu, ponieważ `Employee` dziedziczy `Person` .

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

Poniższy przykład ilustruje zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsie. Klasa `PersonComparer` implementuje interfejs `IComparer(Of Person)`. Można jednak ponownie użyć tej klasy do porównania sekwencji obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person` .

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

## <a name="see-also"></a>Zobacz też

- [Wariancja w interfejsach ogólnych (Visual Basic)](variance-in-generic-interfaces.md)
