---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: 1d8ddaf5d69d87ff6112b5cbb285f0ccfda724e2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397541"
---
# <a name="workflowidle"></a><span data-ttu-id="cc30f-101">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="cc30f-101">\<workflowIdle></span></span>
<span data-ttu-id="cc30f-102">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="cc30f-102">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
<span data-ttu-id="cc30f-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cc30f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cc30f-104">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc30f-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="cc30f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc30f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="cc30f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc30f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="cc30f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="cc30f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="cc30f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowIdle >**</span><span class="sxs-lookup"><span data-stu-id="cc30f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc30f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc30f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc30f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc30f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cc30f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cc30f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc30f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc30f-112">Attributes</span></span>  
  
|<span data-ttu-id="cc30f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cc30f-113">Attribute</span></span>|<span data-ttu-id="cc30f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cc30f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc30f-115">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="cc30f-115">timeToPersist</span></span>|<span data-ttu-id="cc30f-116">Wartość TimeSpan, która określa czas trwania między czasem, gdy przepływ pracy stanie się bezczynny i jest utrwalany.</span><span class="sxs-lookup"><span data-stu-id="cc30f-116">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="cc30f-117">Wartość domyślna to TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="cc30f-117">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="cc30f-118">Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="cc30f-118">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="cc30f-119">Ten atrybut jest przydatny, jeśli chcesz, aby wystąpienie przepływu pracy było bardziej agresywne i nadal utrzymywać wystąpienie w pamięci tak długo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="cc30f-119">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="cc30f-120">Ten atrybut jest prawidłowy tylko wtedy, gdy jego wartość jest mniejsza niż atrybut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="cc30f-120">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="cc30f-121">Jeśli jest większa, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="cc30f-121">If it is greater, it is ignored.</span></span> <span data-ttu-id="cc30f-122">Jeśli ten atrybut upłynie przed wartością określoną przez atrybut **TimeToUnload** , trwałość musi zostać zakończona przed odładowaniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cc30f-122">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="cc30f-123">Oznacza to, że operacja zwolnienia może zostać opóźniona, dopóki przepływ pracy nie zostanie utrwalony.</span><span class="sxs-lookup"><span data-stu-id="cc30f-123">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="cc30f-124">Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków.</span><span class="sxs-lookup"><span data-stu-id="cc30f-124">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="cc30f-125">Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="cc30f-125">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="cc30f-126">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="cc30f-126">timeToUnload</span></span>|<span data-ttu-id="cc30f-127">Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="cc30f-127">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="cc30f-128">Wartość domyślna to 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="cc30f-128">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="cc30f-129">Zwalnianie przepływu pracy oznacza, że jest również utrwalone.</span><span class="sxs-lookup"><span data-stu-id="cc30f-129">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="cc30f-130">Jeśli ten atrybut ma wartość zero, wystąpienie przepływu pracy jest utrwalane i zwalniane natychmiast po przejściu przepływu pracy w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="cc30f-130">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="cc30f-131">Ustawienie tego atrybutu na TimeSpan. MaxValue skutecznie wyłącza operację Zwolnij.</span><span class="sxs-lookup"><span data-stu-id="cc30f-131">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="cc30f-132">Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.</span><span class="sxs-lookup"><span data-stu-id="cc30f-132">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc30f-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc30f-133">Child Elements</span></span>  
 <span data-ttu-id="cc30f-134">Brak.</span><span class="sxs-lookup"><span data-stu-id="cc30f-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc30f-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc30f-135">Parent Elements</span></span>  
  
|<span data-ttu-id="cc30f-136">Element</span><span class="sxs-lookup"><span data-stu-id="cc30f-136">Element</span></span>|<span data-ttu-id="cc30f-137">Opis</span><span class="sxs-lookup"><span data-stu-id="cc30f-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc30f-138">\<zachowanie > w \<usłudze serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="cc30f-138">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="cc30f-139">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="cc30f-139">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc30f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc30f-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
