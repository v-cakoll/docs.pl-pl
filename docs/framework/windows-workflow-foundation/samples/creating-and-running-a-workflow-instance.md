---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 3bfcde3dd635820fa66d639134a43e5e43186c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-running-a-workflow-instance"></a>Tworzenie i uruchamianie wystąpienia przepływu pracy
Ten przykład przedstawia sposób uruchomienia wystąpienia przepływu pracy. Widoczny jest sposób ją wykonać synchronicznego i asynchronicznego.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.  
  
## <a name="discussion"></a>Omówienie  
 Pierwsza część próbki używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Jest to najbardziej podstawową metodą wykonania przepływu pracy. Przepływy pracy wykonywane przy <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.  
  
 Druga część próbki używa <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication> pozwala na większą kontrolę nad każde wystąpienie, w tym możliwość interakcji z uruchomionym przepływem pracy i Uruchom przepływ pracy asynchronicznie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu WorkflowInvoker i WorkflowApplication](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
