---
title: Działanie LINQ to Objects
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: fca4a94a951c9713a61914de6ef33e0cbb74f75e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43552771"
---
# <a name="linq-to-objects-activity"></a>Działanie LINQ to Objects
W tym przykładzie pokazano, jak utworzyć działanie na potrzeby LINQ to Objects elementy zapytania w kolekcji.  
  
## <a name="activity-details-for-findincollection"></a>Szczegóły działań dla FindInCollection  
 To działanie umożliwia użytkownikom elementy zapytania z kolekcji w pamięci, za pomocą LINQ do obiektów. Należy podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników. To działanie może być używane w połączeniu z <xref:System.Activities.Statements.AddToCollection%601> działań.  
  
 W poniższej tabeli przedstawiono właściwości i zwrócenie wartości dla działania.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|`Collection` Właściwość|Wymagana właściwość, która określa, kolekcji źródłowej.|  
|`Predicate` Właściwość|Wymagana właściwość, która określa filtr dla kolekcji w postaci wyrażenia lambda.|  
|Wartość zwracana|Kolekcja filtrowane.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Przykładowy kod, który używa działania niestandardowe  
 Poniższy przykład kodu wykorzystuje `FindInCollection` niestandardowe działanie, aby znaleźć wszystkie wiersze w kolekcji pracownicy, którzy mają `Role` właściwością `Manager` i `Location` właściwością `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Poniższy kod przedstawia sposób tworzenia program przepływu pracy, który używa działania niestandardowego FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, i <xref:System.Activities.Statements.ForEach%601> działań do wypełnienia kolekcji tymi pracowników, Znajdź wszystkich pracowników, role dla deweloperów, które znajdują się w Redmond, a następnie wykonać iterację wynikowej listy.  
  
```csharp  
// Create the Linq predicate for the find expression  
  
Func<Employee, bool> predicate = e => e.Role == "DEV" && e.Location.Equals("Redmond");  
  
// Create workflow program  
Activity sampleWorkflow = new Sequence  
{  
    Variables = { employees, devsFromRedmond },  
    Activities =  
    {  
        new Assign<IList<Employee>>  
        {  
            To = employees,  
            Value = new LambdaValue<IList<Employee>>(c => new List<Employee>())  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(1, "Employee 1", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(2, "Employee 2", "DEV", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(3, "Employee 3", "PM", "Redmond"))  
        },  
        new AddToCollection<Employee>  
        {  
            Collection = new InArgument<ICollection<Employee>>(employees),  
            Item =  new LambdaValue<Employee>(c => new Employee(4, "Employee 4", "PM", "China"))  
        },  
        new FindInCollection<Employee>  
        {  
            Collections = new InArgument<IEnumerable<Employee>>(employees),  
            Predicate = new LambdaValue<Func<Employee, bool>>(c => predicate),  
            Result = new OutArgument<IList<Employee>>(devsFromRedmond)  
        },  
        new ForEach<Employee>  
        {  
            Values = new InArgument<IEnumerable<Employee>>(devsFromRedmond),  
            Body = new ActivityAction<Employee>  
            {  
                Argument = iterationVariable,  
                Handler = new WriteLine  
                {  
                    Text = new InArgument<string>(env => iterationVariable.Get(env).ToString())  
                }  
            }  
        }  
    }  
};  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToObjects.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](https://go.microsoft.com/fwlink/?LinkID=150380)
