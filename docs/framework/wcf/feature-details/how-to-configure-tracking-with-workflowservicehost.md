---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 5781878270272f5ef894c68dc23b9433029e1d41
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968489"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost
W tym temacie wyjaśniono, jak skonfigurować śledzenie [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] dla przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanego w programie. Jest ona konfigurowana za pośrednictwem pliku Web. config przez określenie zachowania usługi.  
  
### <a name="configure-tracking-in-configuration"></a>Konfiguruj śledzenie w konfiguracji  
  
1. `behavior`Dodaj element <xref:System.Activities.Tracking.EtwTrackingParticipant> using > < w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>              
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Poprzedni przykład konfiguracji dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking`elementu >. Profil śledzenia zawiera zapytania śledzenia umożliwiające uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane w przypadku zmiany stanu wystąpienia przepływu pracy w czasie wykonywania. Poniższy przykład pokazuje, jak utworzyć profil śledzenia.  
  
    ```xml  
    <system.serviceModel>  
        <tracking>   
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>   
       </tracking>  
    </system.serviceModel>  
    ```  
  
     Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurowanie śledzenia w kodzie  
  
1. <xref:System.Activities.Tracking.EtwTrackingParticipant> Dodaj zachowanie<xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> przy użyciu kodu, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Poprzedni przykład kodu dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking`elementu >, jak pokazano w poprzedniej sekcji.  
  
     Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Przykład konfigurowania śledzenia programowo można znaleźć w temacie [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
