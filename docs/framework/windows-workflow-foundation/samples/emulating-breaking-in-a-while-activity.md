---
title: Emulowanie fundamentalne za pewien czas działania
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27264832dd82719d7ccb81e1398df343653515b1
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="emulating-breaking-in-a-while-activity"></a>Emulowanie fundamentalne za pewien czas działania
W przykładzie pokazano sposób podziału pętli mechanizmu z następujących działań: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, i <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Jest to przydatne, ponieważ Windows Workflow Foundation (WF) nie zawiera żadnych działań, aby przerwać wykonywanie tych pętle.  
  
## <a name="scenario"></a>Scenariusz  
 Przykład znajduje pierwszy niezawodnej dostawcy z listy dostawców (wystąpienia `Vendor` klasy). Każdy dostawca ma `ID`, `Name` i określająca sposób niezawodny dostawca jest wartość liczbowa niezawodności. Przykład tworzy niestandardowe działanie o nazwie `FindReliableVendor` który odbiera dwóch parametrów wejściowych (lista dostawców i wartość minimalna niezawodność) i zwraca pierwszy dostawca listy, która spełnia podane kryteria.  
  
## <a name="breaking-a-loop"></a>Fundamentalne pętli  
 Windows Workflow Foundation (WF) nie zawiera działania, aby przerwać pętlę. Przykładowy kod, który umożliwia zrealizowanie fundamentalne pętli przy użyciu <xref:System.Activities.Statements.If> działania i kilku zmiennych. W przykładzie <xref:System.Activities.Statements.While> działanie zostało przerwane po `reliableVendor` zmiennej jest przypisywana wartość innych niż `null`.  
  
 W poniższym przykładzie kodu pokazano, jak próbki dzieli chwilę pętli.  
  
```csharp  
// Iterates while the "i" variable is lower than the size of the list   
// and any reliable Vendor is found.        
new While(env => i.Get(env) < this.Vendors.Get(env).Count && reliableVendor.Get(env) == null)  
{  
    DisplayName = "Main loop. Breaks when a reliable vendor is found",  
    Body = new Sequence  
    {                              
        Activities =  
        {  
            // This is the if used for setting the value of the break value…  
            new If  
            {  
                DisplayName = "Check for a reliable vendor",  
  
                //  If a vendor satisfies the reliability level…  
                Condition = new InArgument<bool>(env =>   
                           this.Vendors.Get(env)[i.Get(env)].Reliability >   
                           this.MinimumReliability.Get(env)),  
  
                // then assign that vendor to the reliable vendor variable and   
                // the while condition becomes false (exit the loop).  
                Then = new Assign<Vendor>  
                {  
                    To = reliableVendor,  
                    Value = new InArgument<Vendor>(env =>   
                                  this.Vendors.Get(env)[i.Get(env)])  
                }  
            },  
  
            // Increment the iteration variable.   
            new Assign<int>  
            {  
                DisplayName = "Increment iteration variable",  
                To = i,  
                Value = new InArgument<int>(env => i.Get(env) + 1)  
            }   
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania EmulatingBreakInWhile.sln.  
  
2.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`