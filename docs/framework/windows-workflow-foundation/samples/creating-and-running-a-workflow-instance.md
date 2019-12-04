---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715200"
---
# <a name="creating-and-running-a-workflow-instance"></a>Tworzenie i uruchamianie wystąpienia przepływu pracy

Ten przykład pokazuje, jak uruchomić wystąpienie przepływu pracy. Pokazuje, jak wykonać ją synchronicznie i asynchronicznie.

## <a name="demonstrates"></a>Przedstawia

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Dyskusji

Pierwsza część przykładu używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Jest to najbardziej podstawowy sposób wykonywania przepływu pracy. Przepływy pracy wykonywane z <xref:System.Activities.WorkflowInvoker.Invoke%2A> są wykonywane synchronicznie.

Druga część przykładu używa klasy <xref:System.Activities.WorkflowApplication>. <xref:System.Activities.WorkflowApplication> umożliwia większą kontrolę nad każdym wystąpieniem, w tym możliwość współdziałania z uruchomionym przepływem pracy oraz do asynchronicznego uruchamiania przepływu pracy.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Zobacz także

- [Używanie obiektu WorkflowInvoker i WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
