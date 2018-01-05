---
title: Pobierz WorkflowInstanceId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8fc0edc1e128e03a18c512fc0be03a02537ba71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="get-workflowinstanceid"></a>Pobierz WorkflowInstanceId
W tym przykładzie przedstawiono sposób użycia to niestandardowe działanie `GetWorkflowInstanceId` do zwrócenia identyfikator wystąpienia przepływu pracy.  
  
## <a name="demonstrates"></a>Demonstracje  
 Programowanie działań niestandardowych, jak uzyskać dostępu do wystąpienia przepływu pracy.  
  
## <a name="discussion"></a>Omówienie  
 Pobieranie Identyfikatora wystąpienia uruchomiony przepływ pracy wymaga pisania kodu. Jeśli chcesz zapisać pełni deklaracyjnego przepływu pracy, należy to działanie, które może zwracać identyfikator wystąpienia przepływu pracy, dzięki czemu można odwoływać się działanie w przepływie pracy, aby zapewnić pełni deklaracyjnego przepływu pracy tworzenia. Wiele scenariuszy wymagają dostępu do identyfikator wystąpienia: kilka przykładów dla logowania lub inspekcji lub wykonywania korelacji na poziomie aplikacji, podając identyfikator wystąpienia skojarzenia przyszłych powrót do klienta (na przykład za pomocą tego działania wewnątrz Działanie SendReply).  
  
 `GetWorkflowInstanceId`jest zaimplementowany jako <xref:System.Activities.CodeActivity%601> ponieważ musi zwracać wartość typu <xref:System.Guid>, i musi mieć dostęp do <xref:System.Activities.CodeActivityContext> dla pobierania przepływu pracy wystąpienia identyfikatora. Jej implementacja jest dosyć prosta.  
  
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
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
