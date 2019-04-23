---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1dc186f5899935dab43c0d33894e659c4b19748c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201120"
---
# <a name="workflowidle"></a><span data-ttu-id="7184b-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="7184b-101">\<workflowIdle></span></span>
<span data-ttu-id="7184b-102">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="7184b-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="7184b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7184b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7184b-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="7184b-104">\<behaviors></span></span>  
<span data-ttu-id="7184b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7184b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="7184b-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="7184b-106">\<behavior></span></span>  
<span data-ttu-id="7184b-107">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="7184b-107">\<workflowIdle></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7184b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="7184b-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7184b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7184b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7184b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7184b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7184b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7184b-111">Attributes</span></span>  
  
|<span data-ttu-id="7184b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7184b-112">Attribute</span></span>|<span data-ttu-id="7184b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="7184b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7184b-114">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="7184b-114">timeToPersist</span></span>|<span data-ttu-id="7184b-115">Wartość przedziału czasu, który określa czas trwania między czas przepływu pracy staje się bezczynności i jest trwały.</span><span class="sxs-lookup"><span data-stu-id="7184b-115">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="7184b-116">Wartość domyślna to TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="7184b-116">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="7184b-117">Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="7184b-117">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="7184b-118">Ten atrybut jest przydatna, jeśli chcesz utrwalić wystąpienia przepływu pracy agresywniej jednocześnie zachowując wystąpienie w pamięci tak długo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="7184b-118">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="7184b-119">Ten atrybut jest tylko wtedy, gdy jej wartość jest mniejsza niż **timeToUnload** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7184b-119">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="7184b-120">Jeśli jest większa, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="7184b-120">If it is greater, it is ignored.</span></span> <span data-ttu-id="7184b-121">Jeśli ten atrybut upłynie przed wartość określoną przez **timeToUnload** atrybutu, trwałości przed należy ukończyć przepływ pracy zostanie zwolniony.</span><span class="sxs-lookup"><span data-stu-id="7184b-121">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="7184b-122">Oznacza to, że operacja zwolnienia może być opóźniony, dopóki nie jest trwały przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7184b-122">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="7184b-123">Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7184b-123">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="7184b-124">Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="7184b-124">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="7184b-125">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="7184b-125">timeToUnload</span></span>|<span data-ttu-id="7184b-126">Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="7184b-126">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="7184b-127">Wartość domyślna to 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="7184b-127">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="7184b-128">Zwalnianie przepływu pracy oznacza również utrwalone.</span><span class="sxs-lookup"><span data-stu-id="7184b-128">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="7184b-129">Jeśli ten atrybut jest równa zero wystąpienie przepływu pracy jest trwały i zwolnione natychmiast po przepływ pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="7184b-129">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="7184b-130">Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operacja zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="7184b-130">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="7184b-131">Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.</span><span class="sxs-lookup"><span data-stu-id="7184b-131">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7184b-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7184b-132">Child Elements</span></span>  
 <span data-ttu-id="7184b-133">Brak.</span><span class="sxs-lookup"><span data-stu-id="7184b-133">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7184b-134">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7184b-134">Parent Elements</span></span>  
  
|<span data-ttu-id="7184b-135">Element</span><span class="sxs-lookup"><span data-stu-id="7184b-135">Element</span></span>|<span data-ttu-id="7184b-136">Opis</span><span class="sxs-lookup"><span data-stu-id="7184b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7184b-137">\<zachowanie > z \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7184b-137">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="7184b-138">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="7184b-138">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7184b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7184b-139">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
