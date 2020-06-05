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
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="aff08-102">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff08-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>

<span data-ttu-id="aff08-103">Interfejs współdzielny umożliwia metodom Zwracanie większej liczby typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="aff08-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="aff08-104">Interfejs kontrawariantne umożliwia jej metodom akceptowanie parametrów o mniejszych typach pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="aff08-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>

<span data-ttu-id="aff08-105">W .NET Framework 4, kilka istniejących interfejsów stał się współwariantem i kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="aff08-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="aff08-106">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="aff08-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="aff08-107">Dzięki temu można ponownie użyć metod, które działają z ogólnymi kolekcjami typów podstawowych dla kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="aff08-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>

<span data-ttu-id="aff08-108">Aby uzyskać listę interfejsów wariantów w .NET Framework, zobacz [Wariancja w interfejsach ogólnych (Visual Basic)](variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="aff08-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md).</span></span>

## <a name="converting-generic-collections"></a><span data-ttu-id="aff08-109">Konwertowanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="aff08-109">Converting Generic Collections</span></span>

<span data-ttu-id="aff08-110">Poniższy przykład ilustruje zalety obsługi kowariancji w <xref:System.Collections.Generic.IEnumerable%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="aff08-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="aff08-111">`PrintFullName`Metoda akceptuje kolekcję `IEnumerable(Of Person)` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="aff08-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="aff08-112">Można jednak ponownie użyć go dla kolekcji `IEnumerable(Of Person)` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="aff08-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>

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

## <a name="comparing-generic-collections"></a><span data-ttu-id="aff08-113">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="aff08-113">Comparing Generic Collections</span></span>

<span data-ttu-id="aff08-114">Poniższy przykład ilustruje zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="aff08-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="aff08-115">Klasa `PersonComparer` implementuje interfejs `IComparer(Of Person)`.</span><span class="sxs-lookup"><span data-stu-id="aff08-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="aff08-116">Można jednak ponownie użyć tej klasy do porównania sekwencji obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="aff08-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aff08-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aff08-117">See also</span></span>

- [<span data-ttu-id="aff08-118">Wariancja w interfejsach ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aff08-118">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)
