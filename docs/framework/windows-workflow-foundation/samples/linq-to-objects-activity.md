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
# <a name="linq-to-objects-activity"></a><span data-ttu-id="52184-102">LINQ do obiektów działania</span><span class="sxs-lookup"><span data-stu-id="52184-102">LINQ to Objects Activity</span></span>
<span data-ttu-id="52184-103">Ten przykład przedstawia sposób tworzenia działania na potrzeby LINQ do obiektów z kwerendy elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="52184-103">This sample demonstrates how to create an activity to use LINQ to Objects to query elements in a collection.</span></span>  
  
## <a name="activity-details-for-findincollection"></a><span data-ttu-id="52184-104">Szczegóły działania FindInCollection</span><span class="sxs-lookup"><span data-stu-id="52184-104">Activity Details for FindInCollection</span></span>  
 <span data-ttu-id="52184-105">To działanie umożliwia użytkownikom do zapytania elementów w kolekcji w pamięci za pomocą LINQ do obiektów.</span><span class="sxs-lookup"><span data-stu-id="52184-105">This activity allows users to query elements from collections in memory using LINQ to Objects.</span></span> <span data-ttu-id="52184-106">Należy podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="52184-106">You must provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="52184-107">To działanie może być używane w połączeniu z <xref:System.Activities.Statements.AddToCollection%601> działań.</span><span class="sxs-lookup"><span data-stu-id="52184-107">This activity can be used in conjunction with <xref:System.Activities.Statements.AddToCollection%601> activities.</span></span>  
  
 <span data-ttu-id="52184-108">W poniższej tabeli przedstawiono wartości właściwości i przywrócenie działania.</span><span class="sxs-lookup"><span data-stu-id="52184-108">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="52184-109">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="52184-109">Property or Return Value</span></span>|<span data-ttu-id="52184-110">Opis</span><span class="sxs-lookup"><span data-stu-id="52184-110">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="52184-111">`Collection` Właściwość</span><span class="sxs-lookup"><span data-stu-id="52184-111">`Collection` property</span></span>|<span data-ttu-id="52184-112">Wymaganą właściwość, która określa kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="52184-112">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="52184-113">`Predicate` Właściwość</span><span class="sxs-lookup"><span data-stu-id="52184-113">`Predicate` property</span></span>|<span data-ttu-id="52184-114">Wymaganą właściwość, która określa filtr do kolekcji w postaci wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="52184-114">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="52184-115">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="52184-115">Return Value</span></span>|<span data-ttu-id="52184-116">Filtrowane kolekcji.</span><span class="sxs-lookup"><span data-stu-id="52184-116">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="52184-117">Przykładem kodu, który używa działania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="52184-117">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="52184-118">Poniższy przykład kodu wykorzystuje `FindInCollection` działania niestandardowego można znaleźć w kolekcji pracownicy, którzy mają wszystkie wiersze `Role` ustawioną właściwość `Manager` i `Location` ustawioną właściwość `Redmond`.</span><span class="sxs-lookup"><span data-stu-id="52184-118">The following code example uses the `FindInCollection` custom activity to find all rows in a collection of employees that have a `Role` property set to `Manager` and the `Location` property set to `Redmond`.</span></span>  
  
```csharp  
// Find all program managers in Redmond in the employees collection.  
  
Activity wf = new FindInCollection<Employee>  
{  
    Collections = new LambdaValue<IEnumerable<Employee>>(c => employees),                
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(e => e.Role.Equals("Manager") && e.Location.Equals("Redmond")))  
};  
```  
  
 <span data-ttu-id="52184-119">Poniższy kod przedstawia sposób tworzenia programu przepływu pracy używającego działania niestandardowe FindInCollection <xref:System.Activities.Statements.AddToCollection%601>, i <xref:System.Activities.Statements.ForEach%601> działań do wypełniania kolekcji pracownikom, znajdowanie wszystkich pracowników developer ról, które znajdują się w Redmond, a następnie wykonać iterację wyświetlonej listy.</span><span class="sxs-lookup"><span data-stu-id="52184-119">The following code shows how to create a workflow program that uses the custom FindInCollection activity, <xref:System.Activities.Statements.AddToCollection%601>, and <xref:System.Activities.Statements.ForEach%601> activities to populate a collection with employees, find all the employees that have developer roles and are located in Redmond, and then iterate through the resulting list.</span></span>  
  
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
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="52184-120">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="52184-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="52184-121">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToObjects.sln.</span><span class="sxs-lookup"><span data-stu-id="52184-121">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToObjects.sln solution file.</span></span>  
  
2.  <span data-ttu-id="52184-122">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="52184-122">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="52184-123">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="52184-123">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52184-124">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="52184-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52184-125">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="52184-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52184-126">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="52184-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52184-127">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="52184-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Linq\LinqToObjects`  
  
## <a name="see-also"></a><span data-ttu-id="52184-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52184-128">See Also</span></span>  
 [<span data-ttu-id="52184-129">Wyrażenia lambda (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="52184-129">Lambda Expressions (C# Programming Guide)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150381)  
 [<span data-ttu-id="52184-130">LINQ to Objects</span><span class="sxs-lookup"><span data-stu-id="52184-130">LINQ to Objects</span></span>](http://go.microsoft.com/fwlink/?LinkID=150380)
