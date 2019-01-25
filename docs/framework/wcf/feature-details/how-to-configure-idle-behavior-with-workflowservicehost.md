---
title: 'Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: dff9145954084d0f299edc1e3f2f6c0d7ea1a80e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727394"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost
Przepływy pracy Przejdź bezczynności, po napotkaniu zakładki, która musi być wznowione przez niektóre bodziec zewnętrznych, na przykład gdy wystąpienie przepływu pracy oczekuje na być dostarczane za pomocą wiadomości <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> jest to zachowanie, która umożliwia określenie czasu między gdy wystąpienie usługi wprowadzona bezczynności i gdy wystąpienie jest utrwalona lub zwolnione. Zawiera ona dwie właściwości, które umożliwiają skonfigurowanie tych okresów. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Określa przedział czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a gdy wystąpienie usługi przepływu pracy jest trwały. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Określa przedział czasu między wystąpieniem usługi przepływu pracy przechodzi bezczynności i gdy wystąpienie usługi przepływu pracy jest zwalniana, gdzie zwolnienie oznacza, że utrwalanie wystąpienia magazyn wystąpienia i usunięcie go z pamięci. W tym temacie opisano sposób konfigurowania <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracji.  
  
### <a name="to-configure-workflowidlebehavior"></a>Aby skonfigurować WorkflowIdleBehavior  
  
1.  Dodaj <`workflowIdle`> elementu <`behavior`> elemencie <`serviceBehaviors`> elementu, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` Atrybut określa okres czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a kiedy usługi przepływu pracy jest zwalniana. `timeToPersist` Atrybut określa okres czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a gdy wystąpienie usługi przepływu pracy jest trwały. Wartością domyślną dla `timeToUnload` to 1 minuta. Wartością domyślną dla `timeToPersist` jest <xref:System.TimeSpan.MaxValue>. Jeśli chcesz zachować bezczynności wystąpień w pamięci, ale są przechowywane ich niezawodności, ustaw wartości tak, aby `timeToPersist`  <  `timeToUnload`. Jeśli chcesz uniemożliwić wystąpienia bezczynności Trwa zwalnianie, ustaw `timeToUnload` do <xref:System.TimeSpan.MaxValue>. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  Poprzedni przykład konfiguracji używa uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Aby zmienić zachowanie bezczynności w kodzie  
  
-   Poniższy przykład zmienia czas oczekiwania przed utrwaleniem i wyładowywanie programowo.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
