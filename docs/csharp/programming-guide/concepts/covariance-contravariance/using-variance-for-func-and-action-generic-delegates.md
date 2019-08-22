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
# <a name="using-variance-for-func-and-action-generic-delegates-c"></a><span data-ttu-id="fb5ba-102">Korzystanie z wariancji dla delegatów dla funkcjiC#Func i Action ()</span><span class="sxs-lookup"><span data-stu-id="fb5ba-102">Using Variance for Func and Action Generic Delegates (C#)</span></span>
<span data-ttu-id="fb5ba-103">W poniższych przykładach pokazano, jak używać kowariancji i kontrawariancja `Func` w `Action` i delegatów ogólnych, aby umożliwić ponowne użycie metod i zapewnić większą elastyczność w kodzie.</span><span class="sxs-lookup"><span data-stu-id="fb5ba-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="fb5ba-104">Aby uzyskać więcej informacji na temat kowariancji i kontrawariancja, zobacz [WARIANCJAC#w delegatach ()](./variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fb5ba-104">For more information about covariance and contravariance, see [Variance in Delegates (C#)](./variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="fb5ba-105">Używanie delegatów z parametrami typu współwariantowego</span><span class="sxs-lookup"><span data-stu-id="fb5ba-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="fb5ba-106">Poniższy przykład ilustruje zalety obsługi kowariancji w delegatach ogólnych `Func` .</span><span class="sxs-lookup"><span data-stu-id="fb5ba-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="fb5ba-107">Metoda przyjmuje parametr `String` typu i `Employee` zwraca obiekt typu. `FindByTitle`</span><span class="sxs-lookup"><span data-stu-id="fb5ba-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="fb5ba-108">Można jednak przypisać tę metodę do `Func<String, Person>` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="fb5ba-108">However, you can assign this method to the `Func<String, Person>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="fb5ba-109">Korzystanie z delegatów z parametrami typu kontrawariantne</span><span class="sxs-lookup"><span data-stu-id="fb5ba-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="fb5ba-110">Poniższy przykład ilustruje zalety obsługi kontrawariancja w delegatach ogólnych `Action` .</span><span class="sxs-lookup"><span data-stu-id="fb5ba-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="fb5ba-111">Metoda przyjmuje parametr `Person`typu. `AddToContacts`</span><span class="sxs-lookup"><span data-stu-id="fb5ba-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="fb5ba-112">Można jednak przypisać tę metodę do `Action<Employee>` delegata, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="fb5ba-112">However, you can assign this method to the `Action<Employee>` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb5ba-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb5ba-113">See also</span></span>

- [<span data-ttu-id="fb5ba-114">Kowariancja i kontrawariancja (C#)</span><span class="sxs-lookup"><span data-stu-id="fb5ba-114">Covariance and Contravariance (C#)</span></span>](./index.md)
- [<span data-ttu-id="fb5ba-115">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="fb5ba-115">Generics</span></span>](../../../../standard/generics/index.md)
