---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151848"
---
# <a name="workflowidle"></a><span data-ttu-id="62128-101">\<> przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="62128-101">\<workflowIdle></span></span>
<span data-ttu-id="62128-102">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="62128-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="62128-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="62128-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="62128-104">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="62128-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="62128-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="62128-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="62128-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="62128-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="62128-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="62128-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="62128-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>przepływu pracyIdle**</span><span class="sxs-lookup"><span data-stu-id="62128-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62128-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="62128-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62128-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="62128-110">Attributes and Elements</span></span>  
 <span data-ttu-id="62128-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="62128-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62128-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="62128-112">Attributes</span></span>  
  
|<span data-ttu-id="62128-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="62128-113">Attribute</span></span>|<span data-ttu-id="62128-114">Opis</span><span class="sxs-lookup"><span data-stu-id="62128-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62128-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="62128-115">timeToPersist</span></span>|<span data-ttu-id="62128-116">Wartość Timespan, która określa czas trwania między czasem przepływu pracy staje się bezczynny i jest utrwalony.</span><span class="sxs-lookup"><span data-stu-id="62128-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="62128-117">Wartością domyślną jest TimeSpan.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="62128-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="62128-118">Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="62128-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="62128-119">Ten atrybut jest przydatne, jeśli chcesz utrwalić wystąpienie przepływu pracy bardziej agresywnie, zachowując wystąpienie w pamięci tak długo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="62128-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="62128-120">Ten atrybut jest prawidłowy tylko wtedy, gdy jego wartość jest mniejsza niż **timeToUnload** atrybut.</span><span class="sxs-lookup"><span data-stu-id="62128-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="62128-121">Jeśli jest większa, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="62128-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="62128-122">Jeśli ten atrybut upłynie przed wartością określoną przez **timeToUnload** atrybut, trwałość musi zakończyć się przed wyładowania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="62128-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="62128-123">Oznacza to, że operacja zwalniania może być opóźniona, dopóki przepływ pracy nie zostanie utrwalony.</span><span class="sxs-lookup"><span data-stu-id="62128-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="62128-124">Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków.</span><span class="sxs-lookup"><span data-stu-id="62128-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="62128-125">Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="62128-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="62128-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="62128-126">timeToUnload</span></span>|<span data-ttu-id="62128-127">Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="62128-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="62128-128">Wartość domyślna to 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="62128-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="62128-129">Zwalnianie przepływu pracy oznacza, że jest również utrwalony.</span><span class="sxs-lookup"><span data-stu-id="62128-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="62128-130">Jeśli ten atrybut jest ustawiony na zero, wystąpienie przepływu pracy jest utrwalone i zwalniane natychmiast po tym, jak przepływ pracy stanie się bezczynny.</span><span class="sxs-lookup"><span data-stu-id="62128-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="62128-131">Ustawienie tego atrybutu na TimeSpan.MaxValue skutecznie wyłącza operację zwalniania.</span><span class="sxs-lookup"><span data-stu-id="62128-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="62128-132">Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.</span><span class="sxs-lookup"><span data-stu-id="62128-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62128-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="62128-133">Child Elements</span></span>  
 <span data-ttu-id="62128-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="62128-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62128-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="62128-135">Parent Elements</span></span>  
  
|<span data-ttu-id="62128-136">Element</span><span class="sxs-lookup"><span data-stu-id="62128-136">Element</span></span>|<span data-ttu-id="62128-137">Opis</span><span class="sxs-lookup"><span data-stu-id="62128-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62128-138">\<zachowanie> \<usługZachod></span><span class="sxs-lookup"><span data-stu-id="62128-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="62128-139">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="62128-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62128-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62128-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
