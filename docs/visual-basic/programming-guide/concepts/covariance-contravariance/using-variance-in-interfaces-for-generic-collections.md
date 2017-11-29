---
title: Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b8944bf8f6377ddc633f81dccd9f379bf176d9f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="af930-102">Korzystanie z wariancji w interfejsach dla kolekcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af930-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="af930-103">Interfejs kowariantnego umożliwia jego metody do zwrócenia więcej typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="af930-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="af930-104">Interfejs kontrawariantnego umożliwia jego metody zaakceptować parametry typu mniej pochodnego niż warunki określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="af930-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="af930-105">W programie .NET Framework 4, kilka istniejących interfejsów stał się kowariantnego i kontrawariantny.</span><span class="sxs-lookup"><span data-stu-id="af930-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="af930-106">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="af930-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="af930-107">Dzięki temu można ponownie użyć metody, które pracują z kolekcji typów podstawowych, kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="af930-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="af930-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="af930-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="af930-109">Konwertowanie na kolekcje ogólne</span><span class="sxs-lookup"><span data-stu-id="af930-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="af930-110">Poniższy przykład przedstawia zalet obsługę Kowariancja w <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af930-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="af930-111">`PrintFullName` Metoda przyjmuje Kolekcja `IEnumerable(Of Person)` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="af930-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="af930-112">Jednak można użyć ponownie go z kolekcji `IEnumerable(Of Person)` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="af930-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="af930-113">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="af930-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="af930-114">Poniższy przykład przedstawia świadczenia pomocy technicznej kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af930-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="af930-115">`PersonComparer` Klasa implementuje `IComparer(Of Person)` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="af930-115">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="af930-116">Jednak można ponownie użyć tej klasy, aby porównać sekwencję obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="af930-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarhcy of classes.  
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
  
## <a name="see-also"></a><span data-ttu-id="af930-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af930-117">See Also</span></span>  
 [<span data-ttu-id="af930-118">Wariancje w interfejsach (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af930-118">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
