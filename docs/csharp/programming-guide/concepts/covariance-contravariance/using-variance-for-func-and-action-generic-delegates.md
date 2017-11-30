---
title: "Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1b12a08579f70a07ebb90bfe723209b9f03460e9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="d8bfe-102">Korzystanie z wariancji dla Func i akcji Delegaty ogólne (C#)</span><span class="sxs-lookup"><span data-stu-id="d8bfe-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="d8bfe-103">Poniższe przykłady pokazują, jak używać Kowariancja i kontrawariancja w `Func` i `Action` delegaty ogólne, aby umożliwić ponowne użycie metody i zapewniają większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="d8bfe-104">Aby uzyskać więcej informacji dotyczących kowariancji i kontrawariancji, zobacz [wariancji w Delegatach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d8bfe-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="d8bfe-105">Używanie delegatów z parametrami typu kowariantnego</span><span class="sxs-lookup"><span data-stu-id="d8bfe-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="d8bfe-106">Poniższy przykład przedstawia zalety obsługi Kowariancja w ogólnej `Func` delegatów.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="d8bfe-107">`FindByTitle` Metoda przyjmuje parametr `String` wpisz i zwraca obiekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="d8bfe-108">Jednak można przypisać tę metodę, aby `Func<String, Person>` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="d8bfe-109">Używanie delegatów z parametrami typu kontrawariantnego</span><span class="sxs-lookup"><span data-stu-id="d8bfe-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="d8bfe-110">Poniższy przykład przedstawia zalety obsługi kontrawariancja w ogólnej `Action` delegatów.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="d8bfe-111">`AddToContacts` Metoda przyjmuje parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="d8bfe-112">Jednak można przypisać tę metodę, aby `Action<Employee>` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="d8bfe-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8bfe-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8bfe-113">See Also</span></span>  
 [<span data-ttu-id="d8bfe-114">Kowariancja i Kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="d8bfe-114">Covariance and Contravariance (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="d8bfe-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d8bfe-115">Generics</span></span>](~/docs/standard/generics/index.md)
