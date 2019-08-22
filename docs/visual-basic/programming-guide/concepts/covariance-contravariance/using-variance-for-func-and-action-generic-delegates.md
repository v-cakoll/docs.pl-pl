---
title: Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: ce560f6246469620032ececa4afeeffe69baf407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664360"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="d122f-102">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d122f-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="d122f-103">W poniższych przykładach pokazano, jak używać kowariancji i kontrawariancja `Func` w `Action` i delegatów ogólnych, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d122f-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="d122f-104">Aby uzyskać więcej informacji na temat kowariancji i kontrawariancja, zobacz [Wariancja w delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d122f-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="d122f-105">Używanie delegatów z parametrami typu współwariantowego</span><span class="sxs-lookup"><span data-stu-id="d122f-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="d122f-106">Poniższy przykład ilustruje zalety obsługi kowariancji w delegatach ogólnych `Func` .</span><span class="sxs-lookup"><span data-stu-id="d122f-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="d122f-107">Metoda przyjmuje parametr `String` typu i `Employee` zwraca obiekt typu. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="d122f-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="d122f-108">Można jednak przypisać tę metodę do `Func(Of String, Person)` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="d122f-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="d122f-109">Korzystanie z delegatów z parametrami typu kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="d122f-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="d122f-110">Poniższy przykład ilustruje zalety obsługi kontrawariancja w delegatach ogólnych `Action` .</span><span class="sxs-lookup"><span data-stu-id="d122f-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="d122f-111">Metoda przyjmuje parametr `Person`typu. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="d122f-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="d122f-112">Można jednak przypisać tę metodę do `Action(Of Employee)` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="d122f-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d122f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d122f-113">See also</span></span>

- [<span data-ttu-id="d122f-114">Kowariancja i kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d122f-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="d122f-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d122f-115">Generics</span></span>](../../../../standard/generics/index.md)
