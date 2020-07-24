---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)
description: Dowiedz się, jak używać interfejsów współvariant i kontrawariantne dla kolekcji ogólnych. Zobacz przykłady konwersji i porównywania kolekcji ogólnych.
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: c2ce849e32520cb91422ff36173e418a010476bd
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105676"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="8a637-104">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="8a637-104">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="8a637-105">Interfejs współdzielny umożliwia metodom Zwracanie większej liczby typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8a637-105">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="8a637-106">Interfejs kontrawariantne umożliwia jej metodom akceptowanie parametrów o mniejszych typach pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8a637-106">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="8a637-107">W .NET Framework 4, kilka istniejących interfejsów stał się współwariantem i kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="8a637-107">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="8a637-108">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="8a637-108">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="8a637-109">Dzięki temu można ponownie użyć metod, które działają z ogólnymi kolekcjami typów podstawowych dla kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="8a637-109">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="8a637-110">Aby uzyskać listę interfejsów wariantów w programie .NET, zobacz [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="8a637-110">For a list of variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="8a637-111">Konwertowanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="8a637-111">Converting Generic Collections</span></span>  
 <span data-ttu-id="8a637-112">Poniższy przykład ilustruje zalety obsługi kowariancji w <xref:System.Collections.Generic.IEnumerable%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8a637-112">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="8a637-113">`PrintFullName`Metoda akceptuje kolekcję `IEnumerable<Person>` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8a637-113">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="8a637-114">Można jednak ponownie użyć go dla kolekcji `IEnumerable<Employee>` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="8a637-114">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="8a637-115">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="8a637-115">Comparing Generic Collections</span></span>  
 <span data-ttu-id="8a637-116">Poniższy przykład ilustruje zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="8a637-116">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="8a637-117">Klasa `PersonComparer` implementuje interfejs `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="8a637-117">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="8a637-118">Można jednak ponownie użyć tej klasy do porównania sekwencji obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="8a637-118">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a637-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a637-119">See also</span></span>

- [<span data-ttu-id="8a637-120">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="8a637-120">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
