---
title: Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)
ms.date: 07/20/2015
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
ms.openlocfilehash: b891ccde93e18baf5d5e814911666e9c6268e009
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169743"
---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Używanie wariancji w interfejsach dla kolekcji ogólnych (C#)
Interfejs kowariantny umożliwia jego metody, aby zwrócić więcej typów pochodnych niż określone w interfejsie. Interfejs kontrawariantny umożliwia jego metodom akceptowanie parametrów mniej pochodnych typów niż te określone w interfejsie.  
  
 W .NET Framework 4 kilka istniejących interfejsów stało się kowariantnych i kontrawariantnych. Należą <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.IComparable%601>nich i . Dzięki temu można ponownie użyć metod, które działają z kolekcji ogólnych typów podstawowych dla kolekcji typów pochodnych.  
  
 Aby uzyskać listę interfejsów wariantów w platformie .NET Framework, zobacz [Wariancja w interfejsach ogólnych (C#).](./variance-in-generic-interfaces.md)  
  
## <a name="converting-generic-collections"></a>Konwertowanie kolekcji ogólnych  
 W poniższym przykładzie przedstawiono zalety obsługi <xref:System.Collections.Generic.IEnumerable%601> kowariancji w interfejsie. Metoda `PrintFullName` akceptuje kolekcję `IEnumerable<Person>` typu jako parametr. Można jednak użyć go ponownie dla `IEnumerable<Employee>` kolekcji `Employee` typu, `Person`ponieważ dziedziczy .  
  
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
  
## <a name="comparing-generic-collections"></a>Porównywanie kolekcji ogólnych  
 W poniższym przykładzie przedstawiono zalety obsługi różnic <xref:System.Collections.Generic.IComparer%601> w interfejsie. Klasa `PersonComparer` implementuje interfejs `IComparer<Person>`. Jednak można ponownie użyć tej klasy, aby porównać `Employee` sekwencję obiektów typu, ponieważ `Employee` dziedziczy `Person`.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Wariancja w interfejsach ogólnych (C#)](./variance-in-generic-interfaces.md)
