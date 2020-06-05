---
title: Korzystanie z wariancji dla delegatów ogólnych Func i Action
ms.date: 07/20/2015
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
ms.openlocfilehash: f824d2422d67f1395d21a0863ca8c95d9f108989
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375761"
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="10479-102">Korzystanie z wariancji dla delegatów "Func" i "Action Generic" (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10479-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>

<span data-ttu-id="10479-103">W poniższych przykładach pokazano, jak używać kowariancji i kontrawariancja w `Func` i `Action` delegatów ogólnych, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="10479-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>

<span data-ttu-id="10479-104">Aby uzyskać więcej informacji na temat kowariancji i kontrawariancja, zobacz [Wariancja w delegatach (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="10479-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="10479-105">Używanie delegatów z parametrami typu współwariantowego</span><span class="sxs-lookup"><span data-stu-id="10479-105">Using Delegates with Covariant Type Parameters</span></span>

<span data-ttu-id="10479-106">Poniższy przykład ilustruje zalety obsługi kowariancji w `Func` delegatach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="10479-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="10479-107">`FindByTitle`Metoda przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="10479-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="10479-108">Można jednak przypisać tę metodę do `Func(Of String, Person)` delegata, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="10479-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>

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

## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="10479-109">Korzystanie z delegatów z parametrami typu kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="10479-109">Using Delegates with Contravariant Type Parameters</span></span>

<span data-ttu-id="10479-110">Poniższy przykład ilustruje zalety obsługi kontrawariancja w `Action` delegatach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="10479-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="10479-111">`AddToContacts`Metoda przyjmuje parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="10479-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="10479-112">Można jednak przypisać tę metodę do `Action(Of Employee)` delegata, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="10479-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="10479-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10479-113">See also</span></span>

- [<span data-ttu-id="10479-114">Kowariancja i kontrawariancja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10479-114">Covariance and Contravariance (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="10479-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="10479-115">Generics</span></span>](../../../../standard/generics/index.md)
