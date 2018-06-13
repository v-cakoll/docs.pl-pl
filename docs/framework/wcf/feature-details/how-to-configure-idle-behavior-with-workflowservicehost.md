---
title: 'Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 11992d5e262a23e8f3f29d535e615cfcf57cdc68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492063"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a>Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost
Przepływy pracy Przejdź bezczynności, po napotkaniu zakładki, która musi zostać wznowiony przez niektóre bodźca zewnętrznych, np. gdy wystąpienie przepływu pracy oczekuje na być dostarczane za pomocą wiadomości <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> jest to zachowanie, który umożliwia określenie czasu między po wystąpieniu usługi przechodzi bezczynności i gdy wystąpienie jest utrwalona lub zwalnianie modułu. Zawiera dwie właściwości, które umożliwiają skonfigurowanie tych okresów. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> Określa przedział czasu między po bezczynności przechodzi wystąpienia usługi przepływu pracy i gdy wystąpienie usługi przepływu pracy jest trwały. <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> Określa przedział czasu między gdy przepływ pracy usługi wystąpienie przechodzi bezczynności i gdy wystąpienie usługi przepływu pracy jest zwolniony, gdzie zwolnienie oznacza przechowywanie wystąpienie w magazynie wystąpień i usunięcie go z pamięci. W tym temacie opisano sposób konfigurowania <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracji.  
  
### <a name="to-configure-workflowidlebehavior"></a>Aby skonfigurować WorkflowIdleBehavior  
  
1.  Dodaj <`workflowIdle`> elementu <`behavior`> w elemencie <`serviceBehaviors`> element, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     `timeToUnload` Atrybut określa okres czasu między po bezczynności przechodzi wystąpienia usługi przepływu pracy i kiedy zwolniony jest usługi przepływu pracy. `timeToPersist` Atrybut określa okres czasu między po bezczynności przechodzi wystąpienia usługi przepływu pracy i gdy wystąpienie usługi przepływu pracy jest trwały. Wartość domyślna dla `timeToUnload` to 1 minuta. Wartość domyślna dla `timeToPersist` jest <xref:System.TimeSpan.MaxValue>. Jeśli chcesz zachować bezczynne wystąpienia w pamięci, ale zachowywał je dla niezawodności, ustaw wartości, aby `timeToPersist`  <  `timeToUnload`. Aby zapobiec zwalnianie bezczynne wystąpienia, należy ustawić `timeToUnload` do <xref:System.TimeSpan.MaxValue>. Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
  
    > [!NOTE]
    >  Uproszczona konfiguracja używa powyższego przykładu konfiguracji. Aby uzyskać więcej informacji, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md).  
  
### <a name="to-change-idle-behavior-in-code"></a>Aby zmienić zachowanie bezczynności w kodzie  
  
-   Poniższy przykład umożliwia zmianę czasu oczekiwania przed wprowadzeniem trwałych i zwalnianie programowo.  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
