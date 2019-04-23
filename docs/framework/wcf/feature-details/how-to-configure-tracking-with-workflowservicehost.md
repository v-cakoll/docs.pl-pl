---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: e0631cdb47bc88f7f588f4dfe6c44ea3d44f4e60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59336567"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a>Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost
W tym temacie opisano sposób konfigurowania śledzenia [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] przepływu pracy są hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>. Jest on skonfigurowany za pomocą pliku Web.config, określając zachowanie usługi.  
  
### <a name="configure-tracking-in-configuration"></a>Konfigurowanie śledzenia w konfiguracji  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> element pliku konfiguracji, jak pokazano w poniższym przykładzie.  
  
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
    >  Poprzedni przykład konfiguracji używa uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).  
  
     Dodaje w poprzednim przykładzie konfiguracja <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu. Profile śledzenia są tworzone w <`trackingProfile`> elemencie <`tracking`> element. Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania. Poniższy przykład pokazuje, jak utworzyć profil śledzenia.  
  
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
  
     Aby uzyskać więcej informacji na temat śledzenia profilów, zobacz [profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat śledzenia ogólnie rzecz biorąc, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
### <a name="configure-tracking-in-code"></a>Konfigurowanie śledzenia w kodzie  
  
1. Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> zachowanie w kodzie, jak pokazano w poniższym przykładzie.  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     Poprzedni przykład kodu dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu. Profile śledzenia są tworzone w <`trackingProfile`> elemencie <`tracking`> elementu, jak pokazano w poprzedniej sekcji.  
  
     Aby uzyskać więcej informacji na temat śledzenia profilów, zobacz [profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).  
  
     Aby uzyskać więcej informacji na temat śledzenia ogólnie rzecz biorąc, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md). Przykład konfigurowania śledzenia programowo zobacz [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
## <a name="see-also"></a>Zobacz także

- [Uproszczona konfiguracja usług WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
