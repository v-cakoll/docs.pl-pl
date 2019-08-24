---
title: Tworzenie i uruchamianie wystąpienia przepływu pracy
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: fe00ebec8d81e77ff982a36419f1b0a988fcd4ab
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016044"
---
# <a name="creating-and-running-a-workflow-instance"></a>Tworzenie i uruchamianie wystąpienia przepływu pracy

Ten przykład pokazuje, jak uruchomić wystąpienie przepływu pracy. Pokazuje, jak wykonać ją synchronicznie i asynchronicznie.

## <a name="demonstrates"></a>Demonstracje

<xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.

## <a name="discussion"></a>Dyskusji

Pierwsza część przykładu używa <xref:System.Activities.WorkflowInvoker.Invoke%2A>. Jest to najbardziej podstawowy sposób wykonywania przepływu pracy. Przepływy pracy <xref:System.Activities.WorkflowInvoker.Invoke%2A> wykonywane z programem są wykonywane synchronicznie.

Druga część przykładu używa <xref:System.Activities.WorkflowApplication> klasy. <xref:System.Activities.WorkflowApplication>umożliwia większą kontrolę nad każdym wystąpieniem, w tym możliwość współdziałania z uruchomionym przepływem pracy oraz do asynchronicznego uruchamiania przepływu pracy.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a>Zobacz także

- [Używanie obiektu WorkflowInvoker i WorkflowApplication](../using-workflowinvoker-and-workflowapplication.md)
