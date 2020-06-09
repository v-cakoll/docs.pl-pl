---
title: 'Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8b9fa36408d5f2bc5445ebeccba61f71417935e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599129"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost
Przepływy pracy przechodzą w stan bezczynności, gdy napotkają zakładkę, która musi zostać wznowiona przez jakiś zewnętrzny bodziec, na przykład gdy wystąpienie przepływu pracy oczekuje na dostarczenie wiadomości za pomocą <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>jest zachowaniem, które pozwala określić czas między wystąpieniem usługi, gdy jest ono bezczynne, a wystąpienie jest utrwalane lub zwalniane. Zawiera dwie właściwości, które umożliwiają ustawianie tych okresów. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy zostaje zwolnione, gdzie Unload oznacza trwałe wystąpienie do magazynu wystąpień i usunięcie go z pamięci. W tym temacie opisano sposób konfigurowania programu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracji.  
  
### <a name="to-configure-workflowidlebehavior"></a>Aby skonfigurować WorkflowIdleBehavior  
  
1. Dodaj `workflowIdle` element> <do `behavior` elementu> <w `serviceBehaviors` elemencie <>, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Ten `timeToUnload` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy usługa przepływu pracy zostaje zwolniona. Ten `timeToPersist` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone. Wartość domyślna `timeToUnload` wynosi 1 minutę. Wartość domyślna `timeToPersist` to <xref:System.TimeSpan.MaxValue> . Jeśli chcesz przechowywać bezczynne wystąpienia w pamięci, ale zachowuj ich niezawodność, ustaw wartości tak, aby `timeToPersist`  <  `timeToUnload` . Jeśli chcesz uniemożliwić zwalnianie bezczynnych wystąpień, ustaw wartość `timeToUnload` <xref:System.TimeSpan.MaxValue> . Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , zobacz [Rozszerzalność hosta usługi przepływu pracy](workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Aby zmienić zachowanie bezczynne w kodzie  
  
- Poniższy przykład zmienia czas oczekiwania przed utrwalaniem i wyładowywaniem programowo.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzalność hosta usługi przepływu pracy](workflow-service-host-extensibility.md)
- [Uproszczona konfiguracja](../simplified-configuration.md)
- [Usługi przepływu pracy](workflow-services.md)
