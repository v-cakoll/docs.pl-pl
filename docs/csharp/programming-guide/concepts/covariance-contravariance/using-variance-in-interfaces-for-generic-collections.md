---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 66a1eac33d5f715f52bd83c43bac4452df41aabd
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035334"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="3e9a1-102">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3e9a1-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="3e9a1-103">Kowariantne interfejs umożliwia jego metod zwrócić więcej typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="3e9a1-104">Interfejs kontrawariantnego umożliwia jego metod akceptował parametry typu mniej pochodnego niż warunki określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="3e9a1-105">W programie .NET Framework 4, kilka istniejące interfejsy stało się kowariantne i kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="3e9a1-106">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601>.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="3e9a1-107">Dzięki temu można ponownie użyć metody, które pracują z kolekcji ogólnych typów podstawowych dla kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="3e9a1-108">Aby uzyskać listę interfejsów typu variant w programie .NET Framework, zobacz [wariancje w interfejsach (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="3e9a1-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="3e9a1-109">Konwertowanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="3e9a1-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="3e9a1-110">W poniższym przykładzie pokazano zalety obsługi Kowariancja w <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3e9a1-111">`PrintFullName` Metoda przyjmuje zbiór `IEnumerable<Person>` typu jako parametru.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="3e9a1-112">Jednak można użyć ponownie go kolekcji `IEnumerable<Employee>` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="3e9a1-113">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="3e9a1-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="3e9a1-114">W poniższym przykładzie pokazano zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="3e9a1-115">`PersonComparer` Klasy implementuje `IComparer<Person>` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="3e9a1-116">Jednakże, można ponownie użyć tej klasy, aby porównać sekwencję obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person`.</span><span class="sxs-lookup"><span data-stu-id="3e9a1-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e9a1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e9a1-117">See Also</span></span>

- [<span data-ttu-id="3e9a1-118">Wariancje w interfejsach (C#)</span><span class="sxs-lookup"><span data-stu-id="3e9a1-118">Variance in Generic Interfaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
