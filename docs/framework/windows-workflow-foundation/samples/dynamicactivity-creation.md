---
title: Tworzenie DynamicActivity
ms.date: 03/30/2017
ms.assetid: d8ebe82f-98c8-4452-aed7-2c60a512b097
ms.openlocfilehash: 93435be69f90ca0b74dae6b934cb145fabb7afff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518106"
---
# <a name="dynamicactivity-creation"></a>Tworzenie DynamicActivity
W tym przykładzie pokazano dwa różne sposoby tworzenia działania w czasie wykonywania za pomocą <xref:System.Activities.DynamicActivity> działania.  
  
 W tym przykładzie działanie jest tworzone w czasie wykonywania z treści, która zawiera <xref:System.Activities.Statements.Sequence> działania, który zawiera <xref:System.Activities.Statements.ForEach%601> i <xref:System.Activities.Statements.Assign%601> działań. Listę wejściową liczb całkowitych jest przekazywane do działania i ustawiona jako wartość właściwości. <xref:System.Activities.Statements.ForEach%601> Działanie następnie wykonuje iterację na liście wartości i akumuluje go. W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisz je do średniej.  
  
 Przykład przedstawia użycie <xref:System.Activities.DynamicActivity> wyjściowe działań, przepływającego w zmiennych jako argumenty wejściowe i zwracanie wartości jako argumenty. Działanie ma jeden argument wejściowy o nazwie `Numbers` czyli listę liczb całkowitych. <xref:System.Activities.Statements.ForEach%601> Działanie wykonuje iterację na liście wartości i akumuluje go. W <xref:System.Activities.Statements.Assign%601> działania, średnia wartość jest obliczana przez podzielenie akumulatora przez liczbę elementów na liście i przypisywania go do średniej. Średnia jest zwracana jako wyjściowy argument o nazwie `Average`.  
  
 Podczas tworzenia programowo dynamiczne działania, dane wejściowe i wyjściowe są deklarowane jako, jak pokazano w poniższym przykładzie kodu.  
  
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
  
 Poniższy przykładowy kod przedstawia pełny definicji `DynamicActivity` który oblicza średnią z wartości na liście.  
  
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
  
 Podczas tworzenia w języku XAML, dane wejściowe i wyjściowe są deklarowane jako, jak pokazano w poniższym przykładzie.  
  
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
  
 XAML mogą być tworzone w sposób wizualny przy użyciu [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)]. Jeśli jest włączona w projektu programu Visual Studio, należy ustawić jej "Akcja kompilacji" na "Brak" Aby zapobiec kompilowany. Następnie można załadować pliku XAML dynamicznie za pomocą następujące wywołanie.  
  
```  
Activity act2 = ActivityXamlServices.Load(@"FindAverage.xaml");  
```  
  
 <xref:System.Activities.DynamicActivity> Wystąpienia utworzone programowo lub za pośrednictwem ładowania kodu XAML przepływu pracy można używać jak pokazano w poniższym przykładzie kodu. Należy pamiętać, że "działa" przekazany do `WorkflowInvoker.Invoke` jest "czynnością" <xref:System.Activities.Activity> zdefiniowane w pierwszym przykładzie kodu.  
  
```  
IDictionary<string, object> results = WorkflowInvoker.Invoke(act, new Dictionary<string, object> { { "Numbers", numbers } });  
  
Console.WriteLine("The average calculated using the code activity is = " + results["Average"]);  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania DynamicActivityCreation.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
## <a name="command-line-arguments"></a>Argumenty wiersza polecenia  
 W tym przykładzie akceptuje argumenty wiersza polecenia. Użytkownicy mogą podać listę liczb działania do obliczenia średniej ich. Listę numerów do użycia jest przekazywany jako listę liczb rozdzielonych spacją. Na przykład aby obliczyć średnią 5, 10 lub 32 wywołanie próbki, przy użyciu następującego polecenia.  
  
 **DynamicActivityCreation 5 10 32**  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\DynamicActivityCreation`