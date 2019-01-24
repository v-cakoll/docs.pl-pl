---
title: Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: 134b3c0776e100a4bdc7e902bc8b41477a0ee264
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549460"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="3a510-102">Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a510-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="3a510-103">Te przykłady przedstawiają sposób zastosowania kowariancji i kontrawariancji w `Func` i `Action` delegatów ogólnych, które umożliwiają wielokrotne użycie metod i zapewniają większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3a510-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="3a510-104">Aby uzyskać więcej informacji dotyczących kowariancji i kontrawariancji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3a510-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="3a510-105">Używanie delegatów z Kowariantnymi parametrami typu</span><span class="sxs-lookup"><span data-stu-id="3a510-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="3a510-106">W poniższym przykładzie pokazano zalety obsługi Kowariancja w ogólnej `Func` delegatów.</span><span class="sxs-lookup"><span data-stu-id="3a510-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="3a510-107">`FindByTitle` Metoda przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="3a510-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="3a510-108">Jednak można przypisać tę metodę w celu `Func(Of String, Person)` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="3a510-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class Finder  
    Public Shared Function FindByTitle(  
        ByVal title As String) As Employee  
        ' This is a stub for a method that returns  
        ' an employee that has the specified title.  
        Return New Employee  
    End Function  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim findEmployee As Func(Of String, Employee) =  
            AddressOf FindByTitle  
  
        ' The delegate expects a method to return Person,  
        ' but you can assign it a method that returns Employee.  
        Dim findPerson As Func(Of String, Person) =  
            AddressOf FindByTitle  
  
        ' You can also assign a delegate   
        ' that returns a more derived type to a delegate   
        ' that returns a less derived type.  
        findPerson = findEmployee  
    End Sub  
End Class  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="3a510-109">Używanie delegatów z parametrami kontrawariantnego typu</span><span class="sxs-lookup"><span data-stu-id="3a510-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="3a510-110">W poniższym przykładzie pokazano zalety obsługi kontrawariancja w ogólnej `Action` delegatów.</span><span class="sxs-lookup"><span data-stu-id="3a510-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="3a510-111">`AddToContacts` Metoda przyjmuje parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="3a510-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="3a510-112">Jednak można przypisać tę metodę w celu `Action(Of Employee)` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="3a510-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
```vb  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class AddressBook  
    Shared Sub AddToContacts(ByVal person As Person)  
        ' This method adds a Person object  
        ' to a contact list.  
    End Sub  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim addPersonToContacts As Action(Of Person) =  
            AddressOf AddToContacts  
  
        ' The Action delegate expects   
        ' a method that has an Employee parameter,  
        ' but you can assign it a method that has a Person parameter  
        ' because Employee derives from Person.  
        Dim addEmployeeToContacts As Action(Of Employee) =  
            AddressOf AddToContacts  
  
        ' You can also assign a delegate   
        ' that accepts a less derived parameter   
        ' to a delegate that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a510-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a510-113">See also</span></span>
- [<span data-ttu-id="3a510-114">Kowariancja i Kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a510-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="3a510-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="3a510-115">Generics</span></span>](~/docs/standard/generics/index.md)
