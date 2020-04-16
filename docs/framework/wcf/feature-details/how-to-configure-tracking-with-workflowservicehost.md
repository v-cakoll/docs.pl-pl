---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 3f78b77849d6da7dfff3bdcba90bb4d5200186a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464157"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost
W tym temacie wyjaśniono, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] jak skonfigurować <xref:System.ServiceModel.Activities.WorkflowServiceHost>śledzenie przepływu pracy hostowanego w pliku . Jest on konfigurowany za pośrednictwem pliku Web.config przez określenie zachowania usługi.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurowanie śledzenia w konfiguracji  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> za pomocą <`behavior`> element w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.  
  
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
    > W poprzedniej próbce konfiguracji jest obsługiwana uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     W poprzednim przykładzie <xref:System.Activities.Tracking.EtwTrackingParticipant> konfiguracji dodaje i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w `trackingProfile` <> element w <`tracking`> element. Profil śledzenia zawiera zapytania śledzenia, które umożliwiają uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane, gdy stan wystąpienia przepływu pracy zmienia się w czasie wykonywania. W poniższym przykładzie pokazano, jak utworzyć profil śledzenia.  
  
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
  
     Aby uzyskać więcej informacji na temat profili śledzenia, zobacz [Śledzenie profili](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat śledzenia w ogóle, zobacz [Śledzenie przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurowanie śledzenia w kodzie  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> zachowanie przy użyciu kodu, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Poprzedni przykładowy kod <xref:System.Activities.Tracking.EtwTrackingParticipant> dodaje i określa nazwę profilu śledzenia. Profile śledzenia są tworzone w <`trackingProfile`> element w <`tracking`> element, jak pokazano w poprzedniej sekcji.  
  
     Aby uzyskać więcej informacji na temat profili śledzenia, zobacz [Śledzenie profili](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat śledzenia w ogóle, zobacz [Śledzenie przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Na przykład konfigurowania śledzenia programowo zobacz [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz też

- [Uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
