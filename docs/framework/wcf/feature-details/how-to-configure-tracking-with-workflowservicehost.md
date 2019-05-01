---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: e0631cdb47bc88f7f588f4dfe6c44ea3d44f4e60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039367"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="72d9a-102">Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="72d9a-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="72d9a-103">W tym temacie opisano sposób konfigurowania śledzenia [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] przepływu pracy są hostowane w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="72d9a-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="72d9a-104">Jest on skonfigurowany za pomocą pliku Web.config, określając zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="72d9a-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="72d9a-105">Konfigurowanie śledzenia w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="72d9a-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="72d9a-106">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> element pliku konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="72d9a-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="72d9a-107">Poprzedni przykład konfiguracji używa uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="72d9a-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="72d9a-108">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="72d9a-109">Dodaje w poprzednim przykładzie konfiguracja <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="72d9a-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="72d9a-110">Profile śledzenia są tworzone w <`trackingProfile`> elemencie <`tracking`> element.</span><span class="sxs-lookup"><span data-stu-id="72d9a-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="72d9a-111">Profil śledzenia zawiera śledzenia zapytań, pozwalające uczestnikiem śledzenia do subskrybowania zdarzenia przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72d9a-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="72d9a-112">Poniższy przykład pokazuje, jak utworzyć profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="72d9a-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="72d9a-113">Aby uzyskać więcej informacji na temat śledzenia profilów, zobacz [profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="72d9a-114">Aby uzyskać więcej informacji na temat śledzenia ogólnie rzecz biorąc, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="72d9a-115">Konfigurowanie śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="72d9a-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="72d9a-116">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> zachowanie w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="72d9a-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="72d9a-117">Poprzedni przykład kodu dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="72d9a-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="72d9a-118">Profile śledzenia są tworzone w <`trackingProfile`> elemencie <`tracking`> elementu, jak pokazano w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="72d9a-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="72d9a-119">Aby uzyskać więcej informacji na temat śledzenia profilów, zobacz [profile śledzenia](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="72d9a-120">Aby uzyskać więcej informacji na temat śledzenia ogólnie rzecz biorąc, zobacz [przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="72d9a-121">Przykład konfigurowania śledzenia programowo zobacz [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="72d9a-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d9a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72d9a-122">See also</span></span>

- [<span data-ttu-id="72d9a-123">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="72d9a-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="72d9a-124">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72d9a-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="72d9a-125">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="72d9a-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
