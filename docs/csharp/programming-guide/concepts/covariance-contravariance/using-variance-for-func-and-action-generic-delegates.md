---
title: Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: 903926bc86b1b96cea25b91314e35ed4771bbcb9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880435"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a>Korzystanie z wariancji dla Func i akcji delegatów ogólnych (C#)
Te przykłady przedstawiają sposób zastosowania kowariancji i kontrawariancji w `Func` i `Action` delegatów ogólnych, które umożliwiają wielokrotne użycie metod i zapewniają większą elastyczność w kodzie.  
  
 Aby uzyskać więcej informacji dotyczących kowariancji i kontrawariancji, zobacz [wariancje w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Używanie delegatów z Kowariantnymi parametrami typu  
 W poniższym przykładzie pokazano zalety obsługi Kowariancja w ogólnej `Func` delegatów. `FindByTitle` Metoda przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu. Jednak można przypisać tę metodę w celu `Func<String, Person>` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Używanie delegatów z parametrami kontrawariantnego typu  
 W poniższym przykładzie pokazano zalety obsługi kontrawariancja w ogólnej `Action` delegatów. `AddToContacts` Metoda przyjmuje parametr `Person` typu. Jednak można przypisać tę metodę w celu `Action<Employee>` delegata, ponieważ `Employee` dziedziczy `Person`.  
  
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

- [Kowariancja i Kontrawariancja (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
- [Typy ogólne](~/docs/standard/generics/index.md)
