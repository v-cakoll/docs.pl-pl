---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 571d41194ebc98be81646fb5bfdab060225015ca
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46517950"
---
# <a name="creating-and-running-a-workflow-instance"></a>Tworzenie i uruchamianie wystąpienia przepływu pracy
W tym przykładzie pokazano, jak w celu uruchomienia wystąpienia przepływu pracy. Widoczny jest sposób ją wykonać synchronicznie i asynchronicznie.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>Dyskusja  
 Pierwsza część próbki używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Jest to najprostszy sposób wykonania przepływu pracy. Przepływy pracy, wykonywane przy użyciu <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.  
  
 Druga część próbki używa <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication> pozwala uzyskać większą kontrolę nad każde wystąpienie, w tym możliwość interakcji z uruchomionym przepływem pracy i asynchronicznie Uruchom przepływ pracy.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu WorkflowInvoker i WorkflowApplication](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
