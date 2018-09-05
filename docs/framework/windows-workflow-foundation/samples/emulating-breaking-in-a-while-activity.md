---
title: Przerwanie emulowania w czasu działania
ms.date: 03/30/2017
ms.assetid: ddff715d-d623-4b54-b841-60bacbc3ca21
ms.openlocfilehash: 4938e07364609520f6528688877bce112be26d3f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560428"
---
# <a name="emulating-breaking-in-a-while-activity"></a>Przerwanie emulowania w czasu działania
W tym przykładzie pokazano, jak można przerwać pętli mechanizm następujące działania: <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.While>, i <xref:System.Activities.Statements.ParallelForEach%601>.  
  
 Jest to przydatne, ponieważ Windows Workflow Foundation (WF) nie obejmuje dowolne działanie, aby przerwać wykonywanie tych pętli.  
  
## <a name="scenario"></a>Scenariusz  
 Przykład znajduje pierwszy dostawca niezawodne z listy dostawców (wystąpienia `Vendor` klasy). Każdy dostawca ma `ID`, `Name` i wartość liczbową niezawodności, która określa, jak niezawodny dostawca jest. Przykładowa aplikacja tworzy niestandardowe działanie o nazwie `FindReliableVendor` , otrzymuje dwa parametry wejściowe (lista dostawców i wartość minimalna niezawodność) i zwraca pierwszy dostawca listy, która spełnia podane kryteria.  
  
## <a name="breaking-a-loop"></a>Przerwanie pętli  
 Windows Workflow Foundation (WF) nie ma działania, aby przerwać pętlę. Przykładowy kod w ramach istotne pętlę przy użyciu <xref:System.Activities.Statements.If> działanie i kilku zmiennych. W tym przykładzie <xref:System.Activities.Statements.While> działania nie działa po `reliableVendor` zmienną jest przypisywana wartość innych niż `null`.  
  
 Poniższy przykład kodu demonstruje, jak próbki przerywa chwilę pętli.  
  
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
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania EmulatingBreakInWhile.sln.  
  
2.  Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.  
  
3.  Aby uruchomić rozwiązanie, naciśnij kombinację klawiszy CTRL + F5.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\EmulatingBreakInWhile`