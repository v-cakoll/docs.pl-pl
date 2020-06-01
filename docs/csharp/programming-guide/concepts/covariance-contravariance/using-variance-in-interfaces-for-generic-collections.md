---
title: Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: 5f5531e17a530ed840108df2cf9bf829b2beb656
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241360"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a><span data-ttu-id="3ebb0-102">Korzystanie z wariancji w interfejsach dla kolekcji ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3ebb0-102">Using Variance in Interfaces for Generic Collections (C#)</span></span>
<span data-ttu-id="3ebb0-103">Interfejs współdzielny umożliwia metodom Zwracanie większej liczby typów pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="3ebb0-104">Interfejs kontrawariantne umożliwia jej metodom akceptowanie parametrów o mniejszych typach pochodnych niż określone w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="3ebb0-105">W .NET Framework 4, kilka istniejących interfejsów stał się współwariantem i kontrawariantne.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="3ebb0-106">Obejmują one <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IComparable%601> .</span><span class="sxs-lookup"><span data-stu-id="3ebb0-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="3ebb0-107">Dzięki temu można ponownie użyć metod, które działają z ogólnymi kolekcjami typów podstawowych dla kolekcji typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="3ebb0-108">Aby uzyskać listę interfejsów wariantów w programie .NET, zobacz [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="3ebb0-108">For a list of variant interfaces in .NET, see [Variance in Generic Interfaces (C#)](./variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="3ebb0-109">Konwertowanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="3ebb0-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="3ebb0-110">Poniższy przykład ilustruje zalety obsługi kowariancji w <xref:System.Collections.Generic.IEnumerable%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="3ebb0-111">`PrintFullName`Metoda akceptuje kolekcję `IEnumerable<Person>` typu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-111">The `PrintFullName` method accepts a collection of the `IEnumerable<Person>` type as a parameter.</span></span> <span data-ttu-id="3ebb0-112">Można jednak ponownie użyć go dla kolekcji `IEnumerable<Employee>` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="3ebb0-112">However, you can reuse it for a collection of the `IEnumerable<Employee>` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="comparing-generic-collections"></a><span data-ttu-id="3ebb0-113">Porównywanie kolekcji ogólnych</span><span class="sxs-lookup"><span data-stu-id="3ebb0-113">Comparing Generic Collections</span></span>  
 <span data-ttu-id="3ebb0-114">Poniższy przykład ilustruje zalety obsługi kontrawariancja w <xref:System.Collections.Generic.IComparer%601> interfejsie.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-114">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="3ebb0-115">Klasa `PersonComparer` implementuje interfejs `IComparer<Person>`.</span><span class="sxs-lookup"><span data-stu-id="3ebb0-115">The `PersonComparer` class implements the `IComparer<Person>` interface.</span></span> <span data-ttu-id="3ebb0-116">Można jednak ponownie użyć tej klasy do porównania sekwencji obiektów `Employee` typu, ponieważ `Employee` dziedziczy `Person` .</span><span class="sxs-lookup"><span data-stu-id="3ebb0-116">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ebb0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ebb0-117">See also</span></span>

- [<span data-ttu-id="3ebb0-118">Wariancja w interfejsach ogólnych (C#)</span><span class="sxs-lookup"><span data-stu-id="3ebb0-118">Variance in Generic Interfaces (C#)</span></span>](./variance-in-generic-interfaces.md)
