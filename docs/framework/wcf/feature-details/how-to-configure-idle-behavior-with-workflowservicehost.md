---
title: 'Instrukcje: konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 57a9e0487ff605e99adc22471b02f5a288fc4a2b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912156"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Instrukcje: konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost
Przepływy pracy przechodzą w stan bezczynności, gdy napotkają zakładkę, która musi zostać wznowiona przez jakiś zewnętrzny bodziec, na przykład gdy wystąpienie przepływu pracy oczekuje na dostarczenie wiadomości za pomocą <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>jest zachowaniem, które pozwala określić czas między wystąpieniem usługi, gdy jest ono bezczynne, a wystąpienie jest utrwalane lub zwalniane. Zawiera dwie właściwości, które umożliwiają ustawianie tych okresów. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy zostaje zwolnione, gdzie Unload oznacza trwałe wystąpienie do magazynu wystąpień i usunięcie go z pamięci. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> W tym temacie opisano sposób konfigurowania programu w pliku konfiguracji.  
  
### <a name="to-configure-workflowidlebehavior"></a>Aby skonfigurować WorkflowIdleBehavior  
  
1. Dodaj element >`workflowIdle`< do elementu > <`behavior`w elemencie <`serviceBehaviors`>, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Ten `timeToUnload` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy usługa przepływu pracy zostaje zwolniona. Ten `timeToPersist` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone. Wartość `timeToUnload` domyślna wynosi 1 minutę. Wartość `timeToPersist` domyślna to <xref:System.TimeSpan.MaxValue>. Jeśli chcesz przechowywać bezczynne wystąpienia w pamięci, ale zachowuj ich niezawodność, ustaw wartości tak, aby `timeToPersist`.  <  `timeToUnload` Jeśli chcesz uniemożliwić zwalnianie bezczynnych wystąpień, ustaw wartość `timeToUnload`. <xref:System.TimeSpan.MaxValue> Aby uzyskać więcej informacji <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>na temat, zobacz [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Aby zmienić zachowanie bezczynne w kodzie  
  
- Poniższy przykład zmienia czas oczekiwania przed utrwalaniem i wyładowywaniem programowo.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
