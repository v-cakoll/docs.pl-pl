---
title: Tworzenie działania DynamicActivity
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 270066fafd5c71b2a720ca305433159c172872aa
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534020"
---
# <a name="dynamicactivity-creation"></a>Tworzenie działania DynamicActivity
W tym przykładzie przedstawiono dwa różne sposoby tworzenia działania w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity> działania.  
  
 W tym przykładzie tworzone jest działanie w czasie wykonywania w jednostce, która zawiera <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.Assign%601> działań. Lista wejściowa liczb całkowitych jest przekazywane do działania i ustawić jako właściwość. <xref:System.Activities.Statements.ForEach%601> Działania następnie wykonuje iterację na liście wartości i gromadzi go. W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisz je do średniej.  
  
 W przykładzie pokazano użycie <xref:System.Activities.DynamicActivity> działania, które przechodzą w zmiennych argumentów wejściowych i zwracanie wartości jako dane wyjściowe argumentów. Działanie ma jeden argument wejściowy o nazwie `Numbers` czyli na liście liczb całkowitych. <xref:System.Activities.Statements.ForEach%601> Działanie wykonuje iterację na liście wartości i gromadzi go. W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisywanie jej do średniej. Średnia jest zwracana jako wyjściowy argument o nazwie `Average`.  
  
 Podczas programowego dynamicznego działania, jak pokazano w poniższym przykładzie kodu są deklarowane danych wejściowych i wyjściowych.  
  
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
  
 Poniższy przykład kodu pokazuje kompletną definicję `DynamicActivity` , oblicza średnią z wartości na liście.  
  
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
  
 Podczas tworzenia w XAML, jak pokazano w poniższym przykładzie są deklarowane danych wejściowych i wyjściowych.  
  
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
  
 XAML można tworzyć wizualnie za pomocą [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. Jeśli jest włączona w projekcie programu Visual Studio, należy ustawić jego "Akcja kompilacji" na "None", aby uniemożliwić kompilowanego. XAML może zostać załadowana dynamicznie przy użyciu następującego wywołania.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <xref:System.Activities.DynamicActivity> Programowo utworzyć wystąpienia lub za pośrednictwem ładowania XAML przepływu pracy mogą być używane, jak pokazano w poniższym przykładzie kodu. Należy pamiętać, że "działanie" przekazany do `WorkflowInvoker.Invoke` to "proces" <xref:System.Activities.Activity> zdefiniowane w pierwszym przykładzie kodu.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DynamicActivityCreation.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
## <a name="command-line-arguments"></a>Argumenty wiersza polecenia  
 W tym przykładzie akceptuje argumenty wiersza polecenia. Użytkownicy mogą podać listę liczb dla działania do obliczenia średniej ich. Listę numerów ma być używany jest przekazywany jako listy liczb rozdzielonych spacją. Na przykład można obliczyć średnią 5, 10 i 32 wywołać przykład za pomocą następującego polecenia.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`