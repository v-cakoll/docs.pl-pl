---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 37dc0cac9c6ac69b9e430677a9c8cf3f47b200eb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716021"
---
# <a name="get-workflowinstanceid"></a>Działanie GetWorkflowInstanceId
Ten przykład ilustruje sposób używania działania niestandardowego, `GetWorkflowInstanceId` do zwrócenia identyfikatora wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Przedstawia  
 Niestandardowe programowanie działań, jak uzyskać dostęp do wystąpienia przepływu pracy.  
  
## <a name="discussion"></a>Dyskusji  
 Pobieranie identyfikatora wystąpienia uruchomionego przepływu pracy wymaga napisania kodu. Jeśli chcesz napisać całkowicie deklaratywny przepływ pracy, potrzebujesz działania, które może zwrócić identyfikator wystąpienia przepływu pracy, aby można było odwołać się do działania w przepływie pracy, aby zapewnić w pełni deklaracyjne środowisko tworzenia przepływu pracy. Wiele scenariuszy wymaga dostępu do identyfikatora wystąpienia: kilka przykładów służy do rejestrowania lub przeprowadzania inspekcji lub w celu przeprowadzenia korelacji na poziomie aplikacji, dostarczając identyfikator wystąpienia z powrotem do klienta w celu przyszłego skojarzenia (na przykład za pomocą tego działania w ramach Działanie SendReply).  
  
 `GetWorkflowInstanceId` jest zaimplementowana jako <xref:System.Activities.CodeActivity%601>, ponieważ musi zwrócić wartość typu <xref:System.Guid>i musi mieć dostęp do <xref:System.Activities.CodeActivityContext> do pobierania identyfikatora wystąpienia przepływu pracy. Jego implementacja jest dość podstawowa.  
  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
