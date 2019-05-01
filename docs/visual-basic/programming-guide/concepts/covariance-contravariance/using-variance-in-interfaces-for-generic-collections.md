---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
ms.openlocfilehash: 3c7cde2baf6d8b163c6765b87d6bebef803eb6ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787247"
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="f5d48-102">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5d48-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>

<span data-ttu-id="f5d48-103">Kowariantne interfejs umożliwia jego metod zwrócić więcej typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="f5d48-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="f5d48-104">Interfejs kontrawariantnego umożliwia jego metod akceptował parametry typu mniej pochodnego niż warunki określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="f5d48-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>

<span data-ttu-id="f5d48-105">W programie .NET Framework 4, kilka istniejące interfejsy stało się kowariantne i kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="f5d48-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="f5d48-106">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="f5d48-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="f5d48-107">Dzięki temu można ponownie użyć metody, które pracują z kolekcji ogólnych typów podstawowych dla kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f5d48-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>

<span data-ttu-id="f5d48-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="f5d48-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>

## <a name="converting-generic-collections"></a><span data-ttu-id="f5d48-109">Konwertowanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="f5d48-109">Converting Generic Collections</span></span>

<span data-ttu-id="f5d48-110">W poniższym przykładzie pokazano zalety obsługi Kowariancja w <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f5d48-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f5d48-111">`PrintFullName` Metoda przyjmuje zbiór `IEnumerable(Of Person)` typu jako parametru.</span><span class="sxs-lookup"><span data-stu-id="f5d48-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="f5d48-112">Jednak można użyć ponownie go kolekcji `IEnumerable(Of Person)` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="f5d48-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>

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

## <a name="comparing-generic-collections"></a><span data-ttu-id="f5d48-113">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="f5d48-113">Comparing Generic Collections</span></span>

<span data-ttu-id="f5d48-114">W poniższym przykładzie pokazano zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f5d48-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="f5d48-115">`PersonComparer` Klasy implementuje `IComparer(Of Person)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f5d48-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="f5d48-116">Jednakże, można ponownie użyć tej klasy, aby porównać sekwencję obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="f5d48-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f5d48-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5d48-117">See also</span></span>

- [<span data-ttu-id="f5d48-118">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5d48-118">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
