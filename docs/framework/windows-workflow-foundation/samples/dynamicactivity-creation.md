---
title: Tworzenie DynamicActivity
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1760324fc7911ebe9b3139f79c65222b54a329d0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="dynamicactivity-creation"></a><span data-ttu-id="5942d-102">Tworzenie DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="5942d-102">DynamicActivity Creation</span></span>
<span data-ttu-id="5942d-103">W tym przykładzie pokazano dwa różne sposoby tworzenia działania w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity> działania.</span><span class="sxs-lookup"><span data-stu-id="5942d-103">This sample demonstrates two different ways to create an activity at runtime using the <xref:System.Activities.DynamicActivity> activity.</span></span>  
  
 <span data-ttu-id="5942d-104">W tym przykładzie działanie jest tworzone w czasie wykonywania z treści, która zawiera <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.Assign%601> działań.</span><span class="sxs-lookup"><span data-stu-id="5942d-104">In this sample, an activity is created at runtime with a body that contains a <xref:System.Activities.Statements.Sequence> activity that contains <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.Assign%601> activities.</span></span> <span data-ttu-id="5942d-105">Listę wejściową liczb całkowitych jest przekazywane do działania i ustawiona jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="5942d-105">An input list of integers is passed into the activity and set as a property.</span></span> <span data-ttu-id="5942d-106"><xref:System.Activities.Statements.ForEach%601> Działanie następnie wykonuje iterację na liście wartości i akumuluje go.</span><span class="sxs-lookup"><span data-stu-id="5942d-106">The <xref:System.Activities.Statements.ForEach%601> activity then iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="5942d-107">W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisz je do średniej.</span><span class="sxs-lookup"><span data-stu-id="5942d-107">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assign it to the average.</span></span>  
  
 <span data-ttu-id="5942d-108">Przykład przedstawia użycie <xref:System.Activities.DynamicActivity> wyjściowe działań, przepływającego w zmiennych jako argumenty wejściowe i zwracanie wartości jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="5942d-108">The sample demonstrates the usage of a <xref:System.Activities.DynamicActivity> activity that flows in variables as input arguments and returning values as output arguments.</span></span> <span data-ttu-id="5942d-109">Działanie ma jeden argument wejściowy o nazwie `Numbers` czyli listę liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="5942d-109">The activity has one input argument named `Numbers` that is a list of integers.</span></span> <span data-ttu-id="5942d-110"><xref:System.Activities.Statements.ForEach%601> Działanie wykonuje iterację na liście wartości i akumuluje go.</span><span class="sxs-lookup"><span data-stu-id="5942d-110">The <xref:System.Activities.Statements.ForEach%601> activity iterates over the list of values and accumulates it.</span></span> <span data-ttu-id="5942d-111">W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisywania go do średniej.</span><span class="sxs-lookup"><span data-stu-id="5942d-111">In the <xref:System.Activities.Statements.Assign%601> activity, the average value is calculated by dividing the accumulator by the number of elements in the list and assigning it to the average.</span></span> <span data-ttu-id="5942d-112">Średnia jest zwracana jako wyjściowy argument o nazwie `Average`.</span><span class="sxs-lookup"><span data-stu-id="5942d-112">The average is returned as an output argument named `Average`.</span></span>  
  
 <span data-ttu-id="5942d-113">Podczas tworzenia programowo dynamiczne działania, dane wejściowe i wyjściowe są deklarowane jako, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5942d-113">When the dynamic activity is created programmatically, the input and output are declared as shown in the following code example.</span></span>  
  
```csharp  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
};  
```  
  
 <span data-ttu-id="5942d-114">Poniższy przykładowy kod przedstawia pełny definicji `DynamicActivity` który oblicza średnią z wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="5942d-114">The following code example shows the complete definition of the `DynamicActivity` that computes the average of the values in a list.</span></span>  
  
```  
DynamicActivity act = new DynamicActivity()  
{  
    DisplayName = "Find average",  
    Properties =   
    {  
        // Input argument  
        new DynamicActivityProperty  
        {  
            Name = "Numbers",  
            Type = typeof(InArgument<List<int>>),  
            Value = numbers  
        },  
        // Output argument  
        new DynamicActivityProperty  
        {  
            Name = "Average",  
            Type = typeof(OutArgument<double>),  
            Value = average  
        }  
    },  
    Implementation = () =>  
        new Sequence  
        {  
            Variables = { result, accumulator },  
            Activities =  
            {  
                new ForEach<int>  
                {  
                    Values =  new ArgumentValue<IEnumerable<int>> { ArgumentName = "Numbers" },                                  
                    Body = new ActivityAction<int>  
                    {  
                        Argument = iterationVariable,  
                        Handler = new Assign<int>  
                        {  
                            To = accumulator,  
                            Value = new InArgument<int>(env => iterationVariable.Get(env) +  accumulator.Get(env))  
                        }  
                    }  
                },  
  
                // Calculate the average and assign to the output argument.  
                new Assign<double>  
                {  
                    To = new ArgumentReference<double> { ArgumentName = "Average" },  
                    Value = new InArgument<double>(env => accumulator.Get(env) / numbers.Get(env).Count<int>())  
                },  
            }  
        }  
};  
```  
  
 <span data-ttu-id="5942d-115">Podczas tworzenia w języku XAML, dane wejściowe i wyjściowe są deklarowane jako, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5942d-115">When created in XAML, the input and output are declared as shown in the following example.</span></span>  
  
```xml  
<Activity x:Class="Microsoft.Samples.DynamicActivityCreation.FindAverage"  
          xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
          xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <x:Members>  
    <x:Property Name="Numbers" Type="InArgument(scg:List(x:Int32))" />  
    <x:Property Name="Average" Type="OutArgument(x:Double)" />  
  </x:Members>  
    ...  
    ...  
</Activity>  
```  
  
 <span data-ttu-id="5942d-116">XAML mogą być tworzone w sposób wizualny przy użyciu [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5942d-116">The XAML can be created visually using the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="5942d-117">Jeśli jest włączona w projektu programu Visual Studio, należy ustawić jej "Akcja kompilacji" na "Brak" Aby zapobiec kompilowany.</span><span class="sxs-lookup"><span data-stu-id="5942d-117">If it is included in a Visual Studio project, be sure to set its "Build Action" to "None" to prevent it from being compiled.</span></span> <span data-ttu-id="5942d-118">Następnie można załadować pliku XAML dynamicznie za pomocą następujące wywołanie.</span><span class="sxs-lookup"><span data-stu-id="5942d-118">The XAML can then be loaded dynamically using the following call.</span></span>  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <span data-ttu-id="5942d-119"><xref:System.Activities.DynamicActivity> Wystąpienia utworzone programowo lub za pośrednictwem ładowania kodu XAML przepływu pracy można używać jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5942d-119">The <xref:System.Activities.DynamicActivity> instance created programmatically or through loading a XAML workflow can be used as shown in the following code example.</span></span> <span data-ttu-id="5942d-120">Należy pamiętać, że "działa" przekazany do `WorkflowInvoker.Invoke` jest "czynnością" <xref:System.Activities.Activity> zdefiniowane w pierwszym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5942d-120">Please note that "act" passed to the `WorkflowInvoker.Invoke` is the "act" <xref:System.Activities.Activity> defined in the first code example.</span></span>  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5942d-121">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="5942d-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="5942d-122">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DynamicActivityCreation.sln.</span><span class="sxs-lookup"><span data-stu-id="5942d-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DynamicActivityCreation.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5942d-123">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="5942d-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5942d-124">Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="5942d-124">To run the solution, press CTRL+F5.</span></span>  
  
## <a name="command-line-arguments"></a><span data-ttu-id="5942d-125">Argumenty wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="5942d-125">Command line arguments</span></span>  
 <span data-ttu-id="5942d-126">W tym przykładzie akceptuje argumenty wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5942d-126">This sample accepts command line arguments.</span></span> <span data-ttu-id="5942d-127">Użytkownicy mogą podać listę liczb działania do obliczenia średniej ich.</span><span class="sxs-lookup"><span data-stu-id="5942d-127">Users can provide a list of numbers for the activity to calculate their average.</span></span> <span data-ttu-id="5942d-128">Listę numerów do użycia jest przekazywany jako listę liczb rozdzielonych spacją.</span><span class="sxs-lookup"><span data-stu-id="5942d-128">The list of numbers to be used is passed as a list of numbers separated by a space.</span></span> <span data-ttu-id="5942d-129">Na przykład aby obliczyć średnią 5, 10 lub 32 wywołanie próbki, przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="5942d-129">For example, to calculate the average of 5, 10, and 32 invoke the sample using the following command line.</span></span>  
  
 <span data-ttu-id="5942d-130">**DynamicActivityCreation 5 10 32**</span><span class="sxs-lookup"><span data-stu-id="5942d-130">**DynamicActivityCreation 5 10 32**</span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="5942d-131">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="5942d-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5942d-132">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="5942d-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5942d-133">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="5942d-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5942d-134">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5942d-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`