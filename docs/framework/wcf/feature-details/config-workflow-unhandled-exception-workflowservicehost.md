---
title: 'Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
ms.openlocfilehash: cd3729019b5371b5313bba3814758c723c0d448a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318750"
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a>Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost
<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> To zachowanie, które można określić akcję do wykonania sytuacji Wystąpił nieobsługiwany wyjątek w przepływie pracy hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. W tym temacie przedstawiono sposób skonfigurowania tego zachowania w pliku konfiguracji.  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a>Aby skonfigurować WorkflowUnhandledExceptionBehavior  
  
1. Dodaj <`workflowUnhandledException`> elementu <`behavior`> elemencie <`serviceBehaviors`> element, przy użyciu `action` atrybutu, aby określić akcję do wykonania po wystąpieniu nieobsługiwanego wyjątku, jak pokazano w poniższym przykładzie.  
  
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
    >  Poprzedni przykład konfiguracji używa uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     `action` Atrybut <`workflowUnhandledException`> element może być ustawiony na jedną z następujących wartości:  
  
     **Porzuć**  
     Przerywa wystąpienia w pamięci bez dotykania stanu utrwalonego wystąpienia, (który jest wycofać do ostatniego punktu utrwalanie).  
  
     **abandonAndSuspend**  
     Przerywa wystąpienia w pamięci i aktualizuje utrwalonego wystąpienia zawieszona.  
  
     **Anuluj**  
     Wywołuje anulowania obsługi dla tego wystąpienia, a następnie przetwarza wystąpienia w pamięci, co może też spowodować usunięcie go z magazynu wystąpień  
  
     **terminate**  
     Kończy wystąpienia w pamięci i usuwa go z magazynu wystąpienia.  
  
     Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
