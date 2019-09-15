---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: f8bd3205f5b7a4b3bae5203dc90a3c393cedcbdd
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989370"
---
# <a name="get-workflowinstanceid"></a>Działanie GetWorkflowInstanceId
Ten przykład ilustruje sposób użycia działania `GetWorkflowInstanceId` niestandardowego w celu zwrócenia identyfikatora wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 Niestandardowe programowanie działań, jak uzyskać dostęp do wystąpienia przepływu pracy.  
  
## <a name="discussion"></a>Dyskusji  
 Pobieranie identyfikatora wystąpienia uruchomionego przepływu pracy wymaga napisania kodu. Jeśli chcesz napisać całkowicie deklaratywny przepływ pracy, potrzebujesz działania, które może zwrócić identyfikator wystąpienia przepływu pracy, aby można było odwołać się do działania w przepływie pracy, aby zapewnić w pełni deklaracyjne środowisko tworzenia przepływu pracy. Wiele scenariuszy wymaga dostępu do identyfikatora wystąpienia: kilka przykładów służy do rejestrowania lub przeprowadzania inspekcji lub w celu przeprowadzenia korelacji na poziomie aplikacji, dostarczając identyfikator wystąpienia z powrotem do klienta w celu przyszłego skojarzenia (na przykład za pomocą tego działania w ramach Działanie SendReply).  
  
 `GetWorkflowInstanceId`jest zaimplementowany jako <xref:System.Activities.CodeActivity%601> , ponieważ musi zwrócić wartość typu <xref:System.Guid>i <xref:System.Activities.CodeActivityContext> musi mieć dostęp do elementu w celu pobrania identyfikatora wystąpienia przepływu pracy. Jego implementacja jest dość podstawowa.  
  
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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
