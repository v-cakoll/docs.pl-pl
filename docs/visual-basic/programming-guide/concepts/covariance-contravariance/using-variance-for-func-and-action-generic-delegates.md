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
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Korzystanie z wariancji dla Func i akcji delegatów ogólnych (Visual Basic)
Te przykłady przedstawiają sposób zastosowania kowariancji i kontrawariancji w `Func` i `Action` delegatów ogólnych, które umożliwiają wielokrotne użycie metod i zapewniają większą elastyczność w kodzie.  
  
 Aby uzyskać więcej informacji dotyczących kowariancji i kontrawariancji, zobacz [wariancje w Delegatach (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Używanie delegatów z Kowariantnymi parametrami typu  
 W poniższym przykładzie pokazano zalety obsługi Kowariancja w ogólnej `Func` delegatów. `FindByTitle` Metoda przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu. Jednak można przypisać tę metodę w celu `Func(Of String, Person)` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Używanie delegatów z parametrami kontrawariantnego typu  
 W poniższym przykładzie pokazano zalety obsługi kontrawariancja w ogólnej `Action` delegatów. `AddToContacts` Metoda przyjmuje parametr `Person` typu. Jednak można przypisać tę metodę w celu `Action(Of Employee)` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Kowariancja i Kontrawariancja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)
- [Typy ogólne](~/docs/standard/generics/index.md)
