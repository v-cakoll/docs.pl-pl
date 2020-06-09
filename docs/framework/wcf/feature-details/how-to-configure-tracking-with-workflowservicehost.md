---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 54594a8f464e77062c658606db6bc941e319f71d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599103"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost
W tym temacie wyjaśniono, jak skonfigurować śledzenie dla [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] przepływu pracy hostowanego w programie <xref:System.ServiceModel.Activities.WorkflowServiceHost> . Jest ona konfigurowana za pośrednictwem pliku Web. config przez określenie zachowania usługi.  
  
### <a name="configure-tracking-in-configuration"></a>Konfiguruj śledzenie w konfiguracji  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> element using> <`behavior` w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../simplified-configuration.md).  
  
     Poprzedni przykład konfiguracji dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking` elementu>. Profil śledzenia zawiera zapytania śledzenia umożliwiające uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane w przypadku zmiany stanu wystąpienia przepływu pracy w czasie wykonywania. Poniższy przykład pokazuje, jak utworzyć profil śledzenia.  
  
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
  
     Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurowanie śledzenia w kodzie  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> zachowanie przy użyciu <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> kodu, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Poprzedni przykład kodu dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking` elementu>, jak pokazano w poprzedniej sekcji.  
  
     Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../windows-workflow-foundation/workflow-tracking-and-tracing.md). Przykład konfigurowania śledzenia programowo można znaleźć w temacie [Konfigurowanie śledzenia dla przepływu pracy](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też

- [Uproszczona konfiguracja usług WCF](../samples/simplified-configuration-for-wcf-services.md)
- [Usługi przepływu pracy](workflow-services.md)
- [Profile śledzenia](../../windows-workflow-foundation/tracking-profiles.md)
