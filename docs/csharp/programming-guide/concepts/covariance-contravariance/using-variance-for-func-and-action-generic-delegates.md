---
title: Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 17f55d594ad4364fd29c8f6e41bd6ad2445b0986
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169795"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Używanie wariancji dla delegatów ogólnych akcji i akcji (C#)
W tych przykładach pokazano, jak używać kowariancji `Func` `Action` i kontrawariancji w delegatów i ogólne, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.  
  
 Aby uzyskać więcej informacji na temat kowariancji i kontrawaracji, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Korzystanie z delegatów z parametrami typu kowariantnego  
 Poniższy przykład ilustruje korzyści z obsługi `Func` kowariancji w delegatów ogólnych. Metoda `FindByTitle` przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu. Jednak można przypisać tę metodę `Func<String, Person>` do pełnomocnika, ponieważ `Employee` dziedziczy `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static Employee FindByTitle(String title)  
    {  
        // This is a stub for a method that returns  
        // an employee that has the specified title.  
        return new Employee();  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Func<String, Employee> findEmployee = FindByTitle;  
  
        // The delegate expects a method to return Person,  
        // but you can assign it a method that returns Employee.  
        Func<String, Person> findPerson = FindByTitle;  
  
        // You can also assign a delegate
        // that returns a more derived type
        // to a delegate that returns a less derived type.  
        findPerson = findEmployee;  
  
    }  
}  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Używanie delegatów z parametrami typu contravariant  
 Poniższy przykład ilustruje korzyści z obsługi contravariance w delegatów ogólnych. `Action` Metoda `AddToContacts` przyjmuje parametr `Person` typu. Jednak można przypisać tę metodę `Action<Employee>` do pełnomocnika, ponieważ `Employee` dziedziczy `Person`.  
  
```csharp  
public class Person { }  
public class Employee : Person { }  
class Program  
{  
    static void AddToContacts(Person person)  
    {  
        // This method adds a Person object  
        // to a contact list.  
    }  
  
    static void Test()  
    {  
        // Create an instance of the delegate without using variance.  
        Action<Person> addPersonToContacts = AddToContacts;  
  
        // The Action delegate expects
        // a method that has an Employee parameter,  
        // but you can assign it a method that has a Person parameter  
        // because Employee derives from Person.  
        Action<Employee> addEmployeeToContacts = AddToContacts;  
  
        // You can also assign a delegate
        // that accepts a less derived parameter to a delegate
        // that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts;  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kowariancja i kontrawariancja (C#)](./index.md)
- [Typy ogólne](../../../../standard/generics/index.md)
