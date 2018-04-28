---
title: 'Porady: Konfigurowanie śledzenia przy użyciu klasy WorkflowServiceHost'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cf4b9055334d68337e6414f25f30561b990c732
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="8977f-102">Porady: Konfigurowanie śledzenia przy użyciu klasy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="8977f-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="8977f-103">W tym temacie opisano sposób konfigurowania śledzenia dla [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] przepływu pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="8977f-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="8977f-104">Jest on skonfigurowany za pomocą pliku Web.config, określając zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="8977f-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="8977f-105">Konfigurowanie śledzenia w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8977f-105">Configure Tracking in Configuration</span></span>  
  
1.  <span data-ttu-id="8977f-106">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <`behavior`> w pliku konfiguracji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8977f-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
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
    >  <span data-ttu-id="8977f-107">Uproszczona konfiguracja używa powyższego przykładu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="8977f-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="8977f-108">Aby uzyskać więcej informacji, zobacz [uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="8977f-109">Dodaje powyższego przykładu konfiguracji <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="8977f-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8977f-110">Do tworzenia profilów śledzenia <`trackingProfile`> w elemencie <`tracking`> elementu.</span><span class="sxs-lookup"><span data-stu-id="8977f-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="8977f-111">Profil śledzenia zawiera zapytania dotyczące śledzenia, które umożliwiają śledzenie uczestnika do subskrybowanie zdarzeń przepływu pracy, które są emitowane po zmianie stanu wystąpienia przepływu pracy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8977f-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="8977f-112">Poniższy przykład przedstawia sposób tworzenia profilu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8977f-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8977f-113"> Śledzenie profilów, zobacz [śledzenia profile](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-113"> tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8977f-114"> Ogólnie rzecz biorąc, śledzenie Zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-114"> tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="8977f-115">Konfigurowanie śledzenia w kodzie</span><span class="sxs-lookup"><span data-stu-id="8977f-115">Configure Tracking in Code</span></span>  
  
1.  <span data-ttu-id="8977f-116">Dodaj <xref:System.Activities.Tracking.EtwTrackingParticipant> przy użyciu <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> zachowanie w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8977f-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="8977f-117">Dodaje w poprzednim przykładzie kodu <xref:System.Activities.Tracking.EtwTrackingParticipant> i określa śledzenia nazwy profilu.</span><span class="sxs-lookup"><span data-stu-id="8977f-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="8977f-118">Do tworzenia profilów śledzenia <`trackingProfile`> w elemencie <`tracking`> element, jak pokazano w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8977f-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8977f-119"> Śledzenie profilów, zobacz [śledzenia profile](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-119"> tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="8977f-120"> Ogólnie rzecz biorąc, śledzenie Zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-120"> tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="8977f-121">Aby uzyskać przykład konfigurowania śledzenia programowo zobacz [Konfigurowanie śledzenia przepływu pracy](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8977f-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8977f-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8977f-122">See Also</span></span>  
 [<span data-ttu-id="8977f-123">Uproszczona konfiguracja usług WCF</span><span class="sxs-lookup"><span data-stu-id="8977f-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)  
 [<span data-ttu-id="8977f-124">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8977f-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="8977f-125">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8977f-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
