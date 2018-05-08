---
title: Obsługa anulowania w działaniu Compensable
ms.date: 03/30/2017
ms.assetid: afd98bee-eccf-47e9-99c9-27cea84ce5ce
ms.openlocfilehash: ce4d67b26a2b4c6a9b507715b48e75e328c5b100
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cancellation-handler-on-compensable-activity"></a>Obsługa anulowania w działaniu Compensable
W tym przykładzie przedstawiono użycie obsługi anulowania z <xref:System.Activities.Statements.CompensableActivity>.  
  
 Ten przykład zawiera dwa scenariusze, które przedstawiają sposób używania <xref:System.Activities.Statements.CompensableActivity> anulowania. Pierwszy scenariusz zawiera compensable działania głównego, który zawiera trzy podrzędne działania compensable. Dwa działania podrzędne zakończyć ich jednostki działanie pomyślnie. Po uruchomieniu trzeci treści działania podrzędne napotkał wyjątek, który jest obsługiwany przez anulowanie trzeci przetwarzania działania, po czym zostanie wywołany anulowania działania głównego. Logikę działania głównego, w tym przykładzie jest odpowiednio innych działań podrzędnych dwóch wykonanych wcześniej.  
  
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
  
 Drugi scenariusz zademonstrowano wykonywanie <xref:System.Activities.Statements.TryCatch> równolegle z <xref:System.Activities.Statements.Delay>, która kończy się przed <xref:System.Activities.Statements.TryCatch> gałęzi. Warunek zakończenia ma ustawioną wartość `true` po zakończeniu pierwszej gałęzi, co powoduje innej gałęzi do anulowania.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz CompensationCancellation.sln.  
  
2.  Tworzyć przykładowy kod, naciskając klawisze CTRL + SHIFT + B lub wybierz polecenie "Kompiluj rozwiązanie" z menu kompilacji...  
  
3.  Uruchom próbkę naciskając klawisz F5 lub wybierz polecenie "Rozpocznij debugowanie" z menu Debugowanie. Może również naciśnij klawisze Ctrl + F5 lub wybierz opcję "Uruchom bez debugowania" z menu Debugowanie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CompensationCancellation`