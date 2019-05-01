---
title: Działanie GetWorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005020"
---
# <a name="get-workflowinstanceid"></a>Działanie GetWorkflowInstanceId
W tym przykładzie pokazano, jak użyć niestandardowego działania, `GetWorkflowInstanceId` do zwrócenia identyfikatora wystąpienia przepływu pracy  
  
## <a name="demonstrates"></a>Demonstracje  
 Tworzenie niestandardowego działania, jak dostęp do wystąpienia przepływu pracy.  
  
## <a name="discussion"></a>Dyskusja  
 Identyfikator wystąpienia uruchomiony przepływ pracy wymaga pisania kodu. Jeśli chcesz zapisać pełni deklaracyjnego przepływu pracy, należy działanie, które może zwracać identyfikator wystąpienia przepływu pracy, dzięki czemu mogą być przywoływane działania w przepływie pracy, aby zapewnić w pełni deklaracyjnego przepływu pracy tworzenia. Wiele scenariuszy wymagają dostępu do Identyfikatora wystąpienia: z kilkoma przykładami są rejestrowania lub inspekcji lub wykonując korelacji na poziomie aplikacji, podając identyfikator wystąpienia powrotem do klienta dla przyszłych skojarzenia (na przykład za pomocą tego działania wewnątrz Działanie SendReply).  
  
 `GetWorkflowInstanceId` jest implementowany jako <xref:System.Activities.CodeActivity%601> ponieważ aplikacja musi zwracać wartość typu <xref:System.Guid>, i musi mieć dostęp do <xref:System.Activities.CodeActivityContext> w celu uzyskania przepływu pracy wystąpienia identyfikatora. Jego implementacja jest dosyć.  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
