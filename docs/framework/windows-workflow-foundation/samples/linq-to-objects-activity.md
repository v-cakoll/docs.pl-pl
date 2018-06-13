---
title: LINQ do obiektów działania
ms.date: 03/30/2017
ms.assetid: 403c82e8-7f2b-42f6-93cd-95c35bc76ead
ms.openlocfilehash: e2c2be52a88d8f9a886f0e59c027e1d6c737497c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33516672"
---
# <a name="linq-to-objects-activity"></a>LINQ do obiektów działania
Ten przykład przedstawia sposób tworzenia działania na potrzeby LINQ do obiektów z kwerendy elementów w kolekcji.  
  
## <a name="activity-details-for-findincollection"></a>Szczegóły działania FindInCollection  
 To działanie umożliwia użytkownikom do zapytania elementów w kolekcji w pamięci za pomocą LINQ do obiektów. Należy podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników. To działanie może być używane w połączeniu z <xref:System.Activities.Statements.AddToCollection%601> działań.  
  
 W poniższej tabeli przedstawiono wartości właściwości i przywrócenie działania.  
  
|Właściwości lub wartości zwracanej|Opis|  
|------------------------------|-----------------|  
|`Collection` Właściwość|Wymaganą właściwość, która określa kolekcji źródłowej.|  
|`Predicate` Właściwość|Wymaganą właściwość, która określa filtr do kolekcji w postaci wyrażenia lambda.|  
|Wartość zwracana|Filtrowane kolekcji.|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a>Przykładem kodu, który używa działania niestandardowe  
 Poniższy przykład kodu wykorzystuje `FindInCollection` działania niestandardowego można znaleźć w kolekcji pracownicy, którzy mają wszystkie wiersze `Role` ustawioną właściwość `Manager` i `Location` ustawioną właściwość `Redmond`.  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 Poniższy kod przedstawia sposób tworzenia programu przepływu pracy używającego działania niestandardowe FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, i <xref:System.Activities.Statements.ForEach%601> działań do wypełniania kolekcji pracownikom, znajdowanie wszystkich pracowników developer ról, które znajdują się w Redmond, a następnie wykonać iterację wyświetlonej listy.  
  
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
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToObjects.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisz F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia lambda (C# przewodnik programowania w języku)](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [LINQ to Objects](http://go.microsoft.com/fwlink/?LinkID=150380)
