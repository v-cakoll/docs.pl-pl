---
title: Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: bbfc41fb8ab3e7d800f1eb03098e02056e694872
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659910"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()
W poniższych przykładach pokazano, jak używać kowariancji i kontrawariancja `Func` w `Action` i delegatów ogólnych, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.  
  
 Aby uzyskać więcej informacji na temat kowariancji i kontrawariancja, zobacz [WARIANCJAC#w delegatach ()](./variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Używanie delegatów z parametrami typu współwariantowego  
 Poniższy przykład ilustruje zalety obsługi kowariancji w delegatach ogólnych `Func` . Metoda przyjmuje parametr `String` typu i `Employee` zwraca obiekt typu. `FindByTitle` Można jednak przypisać tę metodę do `Func<String, Person>` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Korzystanie z delegatów z parametrami typu kontrawariantne  
 Poniższy przykład ilustruje zalety obsługi kontrawariancja w delegatach ogólnych `Action` . Metoda przyjmuje parametr `Person`typu. `AddToContacts` Można jednak przypisać tę metodę do `Action<Employee>` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Kowariancja i kontrawariancja (C#)](./index.md)
- [Typy ogólne](../../../../standard/generics/index.md)
