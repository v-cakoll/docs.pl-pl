---
title: 'Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: 69c6b1ce11d735181390a0c67df2f8dbea4f906c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185310"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost
Jest <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> to zachowanie, które umożliwia określenie akcji do podjęcia, jeśli nieobsługiwać <xref:System.ServiceModel.Activities.WorkflowServiceHost>wyjątek występuje w przepływie pracy hostowane w . W tym temacie pokazano, jak skonfigurować to zachowanie w pliku konfiguracyjnym.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Aby skonfigurować przepływ pracyUnhandledExceptionBehavior  
  
1. Dodaj `workflowUnhandledException` <> element w <`behavior`> element w <`serviceBehaviors`> element, przy użyciu atrybutu, `action` aby określić akcję do podjęcia, gdy wystąpi nieobsługiwany wyjątek, jak pokazano w poniższym przykładzie.  
  
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
    > W poprzedniej próbce konfiguracji jest obsługiwana uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     Atrybut `action` <`workflowUnhandledException`> element można ustawić na jedną z następujących wartości:  
  
     **Porzucić**  
     Przerywa wystąpienie w pamięci bez dotykania stanu utrwalone wystąpienie (oznacza to, że wycofać do ostatniego punktu persist).  
  
     **abandonAndSuspend**  
     Przerywa wystąpienie w pamięci i aktualizuje utrwalone wystąpienie do zawieszenia.  
  
     **Anuluj**  
     Wywołuje programy obsługi anulowania dla wystąpienia, a następnie kończy wystąpienie w pamięci, co może również usunąć go z magazynu wystąpień  
  
     **Zakończyć**  
     Kończy wystąpienie w pamięci i usuwa je z magazynu wystąpień.  
  
     Aby uzyskać <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>więcej informacji na temat , zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
