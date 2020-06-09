---
title: 'Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 8b9fa36408d5f2bc5445ebeccba61f71417935e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599129"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="054bf-102">Instrukcje: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="054bf-102">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="054bf-103">Przepływy pracy przechodzą w stan bezczynności, gdy napotkają zakładkę, która musi zostać wznowiona przez jakiś zewnętrzny bodziec, na przykład gdy wystąpienie przepływu pracy oczekuje na dostarczenie wiadomości za pomocą <xref:System.ServiceModel.Activities.Receive> działania.</span><span class="sxs-lookup"><span data-stu-id="054bf-103">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="054bf-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>jest zachowaniem, które pozwala określić czas między wystąpieniem usługi, gdy jest ono bezczynne, a wystąpienie jest utrwalane lub zwalniane.</span><span class="sxs-lookup"><span data-stu-id="054bf-104"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="054bf-105">Zawiera dwie właściwości, które umożliwiają ustawianie tych okresów.</span><span class="sxs-lookup"><span data-stu-id="054bf-105">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="054bf-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone.</span><span class="sxs-lookup"><span data-stu-id="054bf-106"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="054bf-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>określa przedział czasu między kiedy wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy zostaje zwolnione, gdzie Unload oznacza trwałe wystąpienie do magazynu wystąpień i usunięcie go z pamięci.</span><span class="sxs-lookup"><span data-stu-id="054bf-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="054bf-108">W tym temacie opisano sposób konfigurowania programu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="054bf-108">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="054bf-109">Aby skonfigurować WorkflowIdleBehavior</span><span class="sxs-lookup"><span data-stu-id="054bf-109">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="054bf-110">Dodaj `workflowIdle` element> <do `behavior` elementu> <w `serviceBehaviors` elemencie <>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="054bf-110">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="054bf-111">Ten `timeToUnload` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy usługa przepływu pracy zostaje zwolniona.</span><span class="sxs-lookup"><span data-stu-id="054bf-111">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="054bf-112">Ten `timeToPersist` atrybut określa czas, po którym wystąpienie usługi przepływu pracy przechodzi w stan bezczynności i kiedy wystąpienie usługi przepływu pracy jest utrwalone.</span><span class="sxs-lookup"><span data-stu-id="054bf-112">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="054bf-113">Wartość domyślna `timeToUnload` wynosi 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="054bf-113">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="054bf-114">Wartość domyślna `timeToPersist` to <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="054bf-114">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="054bf-115">Jeśli chcesz przechowywać bezczynne wystąpienia w pamięci, ale zachowuj ich niezawodność, ustaw wartości tak, aby `timeToPersist`  <  `timeToUnload` .</span><span class="sxs-lookup"><span data-stu-id="054bf-115">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="054bf-116">Jeśli chcesz uniemożliwić zwalnianie bezczynnych wystąpień, ustaw wartość `timeToUnload` <xref:System.TimeSpan.MaxValue> .</span><span class="sxs-lookup"><span data-stu-id="054bf-116">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="054bf-117">Aby uzyskać więcej informacji na temat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> , zobacz [Rozszerzalność hosta usługi przepływu pracy](workflow-service-host-extensibility.md)</span><span class="sxs-lookup"><span data-stu-id="054bf-117">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="054bf-118">Poprzedni przykład konfiguracji używa uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="054bf-118">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="054bf-119">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="054bf-119">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="054bf-120">Aby zmienić zachowanie bezczynne w kodzie</span><span class="sxs-lookup"><span data-stu-id="054bf-120">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="054bf-121">Poniższy przykład zmienia czas oczekiwania przed utrwalaniem i wyładowywaniem programowo.</span><span class="sxs-lookup"><span data-stu-id="054bf-121">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="054bf-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="054bf-122">See also</span></span>

- [<span data-ttu-id="054bf-123">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="054bf-123">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="054bf-124">Uproszczona konfiguracja</span><span class="sxs-lookup"><span data-stu-id="054bf-124">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="054bf-125">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="054bf-125">Workflow Services</span></span>](workflow-services.md)
