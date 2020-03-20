---
title: 'Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 67be47f97e57792e2f1e14505d3cd121729db33b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185083"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost
Przepływy pracy stają się bezczynne, gdy napotkają zakładkę, która musi zostać wznowiona przez niektóre bodźce zewnętrzne, <xref:System.ServiceModel.Activities.Receive> na przykład gdy wystąpienie przepływu pracy oczekuje na dostarczenie wiadomości przy użyciu działania. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>jest zachowanie, które pozwala określić czas między kiedy wystąpienie usługi przechodzi bezczynnie i gdy wystąpienie jest utrwalone lub zwolniony. Zawiera dwie właściwości, które umożliwiają ustawienie tych przedziałów czasu. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>określa przedział czasu między tym, kiedy wystąpienie usługi przepływu pracy stanie się bezczynne, a wystąpieniem usługi przepływu pracy. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>określa przedział czasu między tym, kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności, a po rozładowaniu wystąpienia usługi przepływu pracy, gdzie zwalnianie oznacza utrwalanie wystąpienia do magazynu wystąpień i usuwanie go z pamięci. W tym temacie wyjaśniono, jak skonfigurować <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracyjnym.  
  
### <a name="to-configure-workflowidlebehavior"></a>Aby skonfigurować zachowanie workflowidleBehavior  
  
1. Dodaj element `workflowIdle`> <do <`behavior`> element w <`serviceBehaviors`> element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Atrybut `timeToUnload` określa okres między tym, kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności, a zwalnianiem usługi przepływu pracy. Atrybut `timeToPersist` określa okres między tym, kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności, a po utrwaleniu wystąpienia usługi przepływu pracy. Wartość domyślna `timeToUnload` to 1 minuta. Wartością domyślną <xref:System.TimeSpan.MaxValue>jest `timeToPersist` . Jeśli chcesz zachować bezczynne wystąpienia w pamięci, ale utrwalić `timeToPersist`  <  `timeToUnload`je dla niezawodności, ustaw wartości tak, aby . Jeśli chcesz zapobiec zwalnianiu bezczynnych wystąpień, `timeToUnload` ustaw <xref:System.TimeSpan.MaxValue>na . Aby uzyskać <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>więcej informacji na temat , zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > W poprzedniej próbce konfiguracji jest obsługiwana uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Aby zmienić zachowanie bezczynne w kodzie  
  
- Poniższy przykład zmienia czas oczekiwania przed utrwalaniem i zwalnianiem programowo.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
