---
title: Procedura obsługi anulowania w działaniu kompensacyjnym
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: 2f32d10e22be7fdd1e84229a214409df06efa918
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442710"
---
# <a name="cancellation-handler-on-compensable-activity"></a>Procedura obsługi anulowania w działaniu kompensacyjnym
Niniejszy przykład pokazuje użycie obsługi anulowania w <xref:System.Activities.Statements.CompensableActivity>.  
  
 Ten przykład zawiera dwa scenariusze, które pokazują użycie <xref:System.Activities.Statements.CompensableActivity> anulowania. Pierwszy scenariusz zawiera działanie kompensacyjne głównego, zawierający trzy czynności kompensacyjne podrzędnych. Dwa działania podrzędne zakończyć ich jednostki działanie pomyślnie. Po uruchomieniu trzeci treści działania podrzędne napotka wyjątek, który jest obsługiwany przez anulowanie trzeci przetwarzania działania, po upływie którego jest wyzwalane anulowania działania głównego. Logikę działania głównego, w tym przykładzie jest kompensacji inne działania podrzędne dwóch wykonanych wcześniej.  
  
```  
Try  
{  
    CA   
    {  
        CA1   
        {  
        }  
        CA2  
        {  
        }  
        CA3  
        {  
            //Exception here  
            // Then this will get cancelled  
        }  
  
       // Cancellation for the root activity automatically gets called, which, in turn, adds some logic to revert what was done (Or can decide to actually confirm CA1 & CA2 if the user so desires).  
    }  
}  
Catches {  
// Can do more stuff...  
}  
```  
  
 Drugi scenariusz pokazuje wykonywania <xref:System.Activities.Statements.TryCatch> równolegle z <xref:System.Activities.Statements.Delay>, który zakończy się przed <xref:System.Activities.Statements.TryCatch> gałęzi. Warunek zakończenia jest ustawiony na `true` po zakończeniu pierwszej gałęzi, powodując innej gałęzi zostaną anulowane.  
  
```  
Parallel   
{  
    Branch1   
    {  
        // Small Delay that times out (timeout1) before branch2.  
    }  
    Branch2   
    {  
        CA   
        {  
            CA1   
            {  
            }  
            CA2   
            {  
            }  
            CA3   
            {  
            }  
            If (timeout1)    
            {  
                call Cancel CA  
            }  
        }  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz CompensationCancellation.sln.  
  
2.  Stworzyć próbkę, naciskając klawisze CTRL + SHIFT + B lub menu kompilacja wybierz polecenie "Kompiluj rozwiązanie"...  
  
3.  Uruchom aplikację przykładową, naciskając klawisz F5 lub wybierz pozycję "Uruchom debugowanie" z menu Debugowanie. Może też naciśnij klawisze Ctrl + F5 lub wybierz pozycję "Rozpocznij bez debugowania" z menu Debugowanie.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`