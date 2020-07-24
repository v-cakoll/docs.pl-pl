---
title: Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)
description: Dowiedz się więcej o używaniu kowariancji i kontrawariancja w delegatach elementów Func i Action, aby zapewnić większą elastyczność w kodzie.
ms.date: 07/20/2015
ms.assetid: 1826774f-2b7a-470f-b110-17cfdd6abdae
ms.openlocfilehash: d7174b0f734d10ab69d0936cb5ca4aa2f4fafdf7
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105711"
---
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="d4451-103">Korzystanie z wariancji dla delegatów funkcji Func i Action (C#)</span><span class="sxs-lookup"><span data-stu-id="d4451-103">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="d4451-104">W poniższych przykładach pokazano, jak używać kowariancji i kontrawariancja w `Func` i `Action` delegatów ogólnych, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d4451-104">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="d4451-105">Aby uzyskać więcej informacji na temat kowariancji i kontrawariancja, zobacz [Wariancja w delegatach (C#)](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d4451-105">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="d4451-106">Używanie delegatów z parametrami typu współwariantowego</span><span class="sxs-lookup"><span data-stu-id="d4451-106">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="d4451-107">Poniższy przykład ilustruje zalety obsługi kowariancji w `Func` delegatach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d4451-107">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="d4451-108">`FindByTitle`Metoda przyjmuje parametr `String` typu i zwraca obiekt `Employee` typu.</span><span class="sxs-lookup"><span data-stu-id="d4451-108">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="d4451-109">Można jednak przypisać tę metodę do `Func<String, Person>` delegata, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="d4451-109">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="d4451-110">Korzystanie z delegatów z parametrami typu kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="d4451-110">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="d4451-111">Poniższy przykład ilustruje zalety obsługi kontrawariancja w `Action` delegatach ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d4451-111">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="d4451-112">`AddToContacts`Metoda przyjmuje parametr `Person` typu.</span><span class="sxs-lookup"><span data-stu-id="d4451-112">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="d4451-113">Można jednak przypisać tę metodę do `Action<Employee>` delegata, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="d4451-113">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4451-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4451-114">See also</span></span>

- [<span data-ttu-id="d4451-115">Kowariancja i kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="d4451-115">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="d4451-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="d4451-116">Generics</span></span>](../../../../standard/generics/index.md)
