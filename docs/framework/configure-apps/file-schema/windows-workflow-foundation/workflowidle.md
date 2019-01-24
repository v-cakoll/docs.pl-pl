---
title: '&lt;workflowIdle&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 9d9eb45090367fb2cc18fc357c219e74d63fb667
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628104"
---
# <a name="ltworkflowidlegt"></a><span data-ttu-id="2a6b3-102">&lt;workflowIdle&gt;</span><span class="sxs-lookup"><span data-stu-id="2a6b3-102">&lt;workflowIdle&gt;</span></span>
<span data-ttu-id="2a6b3-103">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-103">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="2a6b3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a6b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a6b3-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="2a6b3-105">\<behaviors></span></span>  
<span data-ttu-id="2a6b3-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2a6b3-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2a6b3-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="2a6b3-107">\<behavior></span></span>  
<span data-ttu-id="2a6b3-108">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="2a6b3-108">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6b3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a6b3-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <workflowIdle timeToPersist="TimeSpan" 
                    timeToUnload="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a6b3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a6b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a6b3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a6b3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a6b3-112">Attributes</span></span>  
  
|<span data-ttu-id="2a6b3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a6b3-113">Attribute</span></span>|<span data-ttu-id="2a6b3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2a6b3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a6b3-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="2a6b3-115">timeToPersist</span></span>|<span data-ttu-id="2a6b3-116">Wartość przedziału czasu, który określa czas trwania między czas przepływu pracy staje się bezczynności i jest trwały.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="2a6b3-117">Wartość domyślna to TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="2a6b3-118">Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="2a6b3-119">Ten atrybut jest przydatna, jeśli chcesz utrwalić wystąpienia przepływu pracy agresywniej jednocześnie zachowując wystąpienie w pamięci tak długo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="2a6b3-120">Ten atrybut jest tylko wtedy, gdy jej wartość jest mniejsza niż **timeToUnload** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="2a6b3-121">Jeśli jest większa, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="2a6b3-122">Jeśli ten atrybut upłynie przed wartość określoną przez **timeToUnload** atrybutu, trwałości przed należy ukończyć przepływ pracy zostanie zwolniony.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="2a6b3-123">Oznacza to, że operacja zwolnienia może być opóźniony, dopóki nie jest trwały przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="2a6b3-124">Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="2a6b3-125">Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2a6b3-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="2a6b3-126">timeToUnload</span></span>|<span data-ttu-id="2a6b3-127">Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="2a6b3-128">Wartość domyślna to 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="2a6b3-129">Zwalnianie przepływu pracy oznacza również utrwalone.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="2a6b3-130">Jeśli ten atrybut jest równa zero wystąpienie przepływu pracy jest trwały i zwolnione natychmiast po przepływ pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="2a6b3-131">Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="2a6b3-132">Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a6b3-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a6b3-133">Child Elements</span></span>  
 <span data-ttu-id="2a6b3-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a6b3-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a6b3-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2a6b3-136">Element</span><span class="sxs-lookup"><span data-stu-id="2a6b3-136">Element</span></span>|<span data-ttu-id="2a6b3-137">Opis</span><span class="sxs-lookup"><span data-stu-id="2a6b3-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a6b3-138">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2a6b3-138">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="2a6b3-139">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="2a6b3-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a6b3-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a6b3-140">See also</span></span>
- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
