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
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="c83eb-102">Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c83eb-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="c83eb-103">W tym temacie wyjaśniono, jak skonfigurować śledzenie [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] dla przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>hostowanego w programie.</span><span class="sxs-lookup"><span data-stu-id="c83eb-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="c83eb-104">Jest ona konfigurowana za pośrednictwem pliku Web. config przez określenie zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c83eb-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="c83eb-105">Konfiguruj śledzenie w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c83eb-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="c83eb-106">`behavior`Dodaj element <xref:System.Activities.Tracking.EtwTrackingParticipant> using > < w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c83eb-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="c83eb-107">Poprzedni przykład konfiguracji używa uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c83eb-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="c83eb-108">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="c83eb-109">Poprzedni przykład konfiguracji dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c83eb-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="c83eb-110">Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking`elementu >.</span><span class="sxs-lookup"><span data-stu-id="c83eb-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="c83eb-111">Profil śledzenia zawiera zapytania śledzenia umożliwiające uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane w przypadku zmiany stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c83eb-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="c83eb-112">Poniższy przykład pokazuje, jak utworzyć profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c83eb-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="c83eb-113">Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="c83eb-114">Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="c83eb-115">Konfigurowanie śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="c83eb-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="c83eb-116"><xref:System.Activities.Tracking.EtwTrackingParticipant> Dodaj zachowanie<xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> przy użyciu kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="c83eb-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="c83eb-117">Poprzedni przykład kodu dodaje <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c83eb-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="c83eb-118">Profile śledzenia są tworzone w <`trackingProfile`> elementu w ramach <`tracking`elementu >, jak pokazano w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c83eb-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="c83eb-119">Aby uzyskać więcej informacji o profilach śledzenia, zobacz [śledzenie profilów](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="c83eb-120">Aby uzyskać więcej informacji na temat ogólnego śledzenia, zobacz [śledzenie i śledzenie przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="c83eb-121">Przykład konfigurowania śledzenia programowo można znaleźć w temacie [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="c83eb-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c83eb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c83eb-122">See also</span></span>

- [<span data-ttu-id="c83eb-123">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="c83eb-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="c83eb-124">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c83eb-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="c83eb-125">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c83eb-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
