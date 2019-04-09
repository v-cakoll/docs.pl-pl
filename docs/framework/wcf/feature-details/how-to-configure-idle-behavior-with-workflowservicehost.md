---
title: 'Instrukcje: konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: d3fc95e7e92d3fc7c149790d4af00a464ab427f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164024"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="ca47a-102">Instrukcje: konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="ca47a-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="ca47a-103">Przepływy pracy Przejdź bezczynności, po napotkaniu zakładki, która musi być wznowione przez niektóre bodziec zewnętrznych, na przykład gdy wystąpienie przepływu pracy oczekuje na być dostarczane za pomocą wiadomości <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="ca47a-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> <span data-ttu-id="ca47a-104">jest to zachowanie, która umożliwia określenie czasu między gdy wystąpienie usługi wprowadzona bezczynności i gdy wystąpienie jest utrwalona lub zwolnione.</span><span class="sxs-lookup"><span data-stu-id="ca47a-104">is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="ca47a-105">Zawiera ona dwie właściwości, które umożliwiają skonfigurowanie tych okresów.</span><span class="sxs-lookup"><span data-stu-id="ca47a-105">It contains two properties that enable you to set these time spans.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> <span data-ttu-id="ca47a-106">Określa przedział czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a gdy wystąpienie usługi przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="ca47a-106">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> <span data-ttu-id="ca47a-107">Określa przedział czasu między wystąpieniem usługi przepływu pracy przechodzi bezczynności i gdy wystąpienie usługi przepływu pracy jest zwalniana, gdzie zwolnienie oznacza, że utrwalanie wystąpienia magazyn wystąpienia i usunięcie go z pamięci.</span><span class="sxs-lookup"><span data-stu-id="ca47a-107">specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="ca47a-108">W tym temacie opisano sposób konfigurowania <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="ca47a-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="ca47a-109">Aby skonfigurować WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="ca47a-109">To configure WorkflowIdleBehavior</span></span>  
  
1.  <span data-ttu-id="ca47a-110">Dodaj <`workflowIdle`> elementu <`behavior`> elemencie <`serviceBehaviors`> elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ca47a-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="ca47a-111">`timeToUnload` Atrybut określa okres czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a kiedy usługi przepływu pracy jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="ca47a-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="ca47a-112">`timeToPersist` Atrybut określa okres czasu między podczas bezczynności przechodzi wystąpienie usługi przepływu pracy, a gdy wystąpienie usługi przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="ca47a-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="ca47a-113">Wartością domyślną dla `timeToUnload` to 1 minuta.</span><span class="sxs-lookup"><span data-stu-id="ca47a-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="ca47a-114">Wartością domyślną dla `timeToPersist` jest <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="ca47a-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="ca47a-115">Jeśli chcesz zachować bezczynności wystąpień w pamięci, ale są przechowywane ich niezawodności, ustaw wartości tak, aby `timeToPersist`  <  `timeToUnload`.</span><span class="sxs-lookup"><span data-stu-id="ca47a-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="ca47a-116">Jeśli chcesz uniemożliwić wystąpienia bezczynności Trwa zwalnianie, ustaw `timeToUnload` do <xref:System.TimeSpan.MaxValue>.</span><span class="sxs-lookup"><span data-stu-id="ca47a-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="ca47a-117">Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="ca47a-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ca47a-118">Poprzedni przykład konfiguracji używa uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="ca47a-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="ca47a-119">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ca47a-119">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="ca47a-120">Aby zmienić zachowanie bezczynności w kodzie</span><span class="sxs-lookup"><span data-stu-id="ca47a-120">To change idle behavior in code</span></span>  
  
-   <span data-ttu-id="ca47a-121">Poniższy przykład zmienia czas oczekiwania przed utrwaleniem i wyładowywanie programowo.</span><span class="sxs-lookup"><span data-stu-id="ca47a-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ca47a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca47a-122">See also</span></span>

- [<span data-ttu-id="ca47a-123">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ca47a-123">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)
- [<span data-ttu-id="ca47a-124">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="ca47a-124">Simplified Configuration</span></span>](../../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="ca47a-125">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ca47a-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
