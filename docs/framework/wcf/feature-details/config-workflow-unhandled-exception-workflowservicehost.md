---
title: "Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ac014e5854f697c73ff8277104f22081c3417391
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Jest zachowanie, które można określić akcję do wykonania, jeśli wystąpi nieobsługiwany wyjątek w przepływie pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W tym temacie przedstawiono sposób skonfigurowania tego zachowania w pliku konfiguracji.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Aby skonfigurować WorkflowUnhandledExceptionBehavior  
  
1.  Dodaj <`workflowUnhandledException`> elementu <`behavior`> w elemencie <`serviceBehaviors`> element, przy użyciu `action` atrybutu, aby określić akcję wykonywaną, gdy wystąpi nieobsługiwany wyjątek, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  Uproszczona konfiguracja używa powyższego przykładu konfiguracji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Atrybut <`workflowUnhandledException`> element może być ustawiony na jedną z następujących wartości:  
  
     **porzucenia**  
     Przerywa wystąpienia w pamięci bez modyfikowania stanu trwałego wystąpienia (tj. Przywracanie do ostatniego punktu utrwalanie).  
  
     **abandonAndSuspend**  
     Przerywa wystąpienia w pamięci i aktualizuje trwałego wystąpienia zostanie zawieszona.  
  
     **Anuluj**  
     Wywołuje anulowania obsługi dla tego wystąpienia, a następnie kończy wystąpienia w pamięci, co może też spowodować usunięcie go z magazynu wystąpień  
  
     **Zakończenie**  
     Kończy wystąpienia w pamięci i usuwa go z magazynu wystąpień.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
