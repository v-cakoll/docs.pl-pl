---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 8cb83fcf15b814b0ca6f7f95f1a9b8eec70185cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142735"
---
# <a name="get-workflowinstanceid"></a>Działanie GetWorkflowInstanceId
W tym przykładzie pokazano, jak `GetWorkflowInstanceId` używać działania niestandardowego, aby zwrócić identyfikator wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 Niestandardowe tworzenie działań, jak uzyskać dostęp do wystąpienia przepływu pracy.  
  
## <a name="discussion"></a>Dyskusji  
 Uzyskanie identyfikatora wystąpienia uruchomionego przepływu pracy wymaga zapisu kodu. Jeśli chcesz napisać w pełni deklaratywny przepływ pracy, potrzebujesz działania, które może zwrócić identyfikator wystąpienia przepływu pracy, aby można było odwoływać się do działania w przepływie pracy, aby zapewnić w pełni deklaratywne środowisko tworzenia przepływu pracy. Wiele scenariuszy wymaga dostępu do identyfikatora wystąpienia: kilka przykładów dotyczy rejestrowania lub inspekcji lub wykonywania korelacji na poziomie aplikacji przez podanie identyfikatora wystąpienia z powrotem do klienta dla przyszłego skojarzenia (na przykład przy użyciu tego działania wewnątrz działania SendReply).  
  
 `GetWorkflowInstanceId`jest implementowany <xref:System.Activities.CodeActivity%601> jako, ponieważ musi zwracać wartość typu <xref:System.Guid>i <xref:System.Activities.CodeActivityContext> musi mieć dostęp do uzyskiwania identyfikatora wystąpienia przepływu pracy. Jego wdrożenie jest dość proste.  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
