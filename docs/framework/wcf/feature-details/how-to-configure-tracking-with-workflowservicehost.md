---
title: 'Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185069"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="502a4-102">Instrukcje: konfigurowanie śledzenia za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="502a4-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="502a4-103">W tym temacie wyjaśniono, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] jak skonfigurować <xref:System.ServiceModel.Activities.WorkflowServiceHost>śledzenie przepływu pracy hostowanego w pliku .</span><span class="sxs-lookup"><span data-stu-id="502a4-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="502a4-104">Jest on konfigurowany za pośrednictwem pliku Web.config przez określenie zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="502a4-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="502a4-105">Konfigurowanie śledzenia w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="502a4-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="502a4-106">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> za pomocą <`behavior`> element w pliku konfiguracyjnym, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="502a4-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    > <span data-ttu-id="502a4-107">W poprzedniej próbce konfiguracji jest obsługiwana uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="502a4-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="502a4-108">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="502a4-109">W poprzednim przykładzie <xref:System.Activities.Tracking.EtwTrackingParticipant> konfiguracji dodaje i określa nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="502a4-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="502a4-110">Profile śledzenia są tworzone w `trackingProfile` <> element w <`tracking`> element.</span><span class="sxs-lookup"><span data-stu-id="502a4-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="502a4-111">Profil śledzenia zawiera zapytania śledzenia, które umożliwiają uczestnikowi śledzenia subskrybowanie zdarzeń przepływu pracy, które są emitowane, gdy stan wystąpienia przepływu pracy zmienia się w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="502a4-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="502a4-112">W poniższym przykładzie pokazano, jak utworzyć profil śledzenia.</span><span class="sxs-lookup"><span data-stu-id="502a4-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="502a4-113">Aby uzyskać więcej informacji na temat profili śledzenia, zobacz [Śledzenie profili](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="502a4-114">Aby uzyskać więcej informacji na temat śledzenia w ogóle, zobacz [Śledzenie przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="502a4-115">Konfigurowanie śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="502a4-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="502a4-116">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> zachowanie przy użyciu kodu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="502a4-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="502a4-117">Poprzedni przykładowy kod <xref:System.Activities.Tracking.EtwTrackingParticipant> dodaje i określa nazwę profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="502a4-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="502a4-118">Profile śledzenia są tworzone w <`trackingProfile`> element w <`tracking`> element, jak pokazano w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="502a4-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="502a4-119">Aby uzyskać więcej informacji na temat profili śledzenia, zobacz [Śledzenie profili](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="502a4-120">Aby uzyskać więcej informacji na temat śledzenia w ogóle, zobacz [Śledzenie przepływu pracy i śledzenie](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="502a4-121">Na przykład konfigurowania śledzenia programowo zobacz [Konfigurowanie śledzenia dla przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="502a4-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502a4-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="502a4-122">See also</span></span>

- [<span data-ttu-id="502a4-123">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="502a4-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="502a4-124">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="502a4-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="502a4-125">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="502a4-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
