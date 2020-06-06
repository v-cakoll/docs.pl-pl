---
title: <workflowIdle>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b2ef703c-3e01-4213-9d2e-c14c7dba94d2
ms.openlocfilehash: d9eb182ef9c35d2e4c6f5d434e6b200ae2e7ca26
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151848"
---
# \<workflowIdle>
<span data-ttu-id="b6dd9-101">Zachowanie usługi sterująca po zwolnione wystąpienia bezczynności przepływu pracy i utrwalone.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-101">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowIdle>**  
  
## <a name="syntax"></a><span data-ttu-id="b6dd9-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6dd9-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6dd9-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6dd9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b6dd9-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6dd9-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6dd9-105">Attributes</span></span>  
  
|<span data-ttu-id="b6dd9-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6dd9-106">Attribute</span></span>|<span data-ttu-id="b6dd9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6dd9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6dd9-108">timeToPersist</span><span class="sxs-lookup"><span data-stu-id="b6dd9-108">timeToPersist</span></span>|<span data-ttu-id="b6dd9-109">Wartość TimeSpan, która określa czas trwania między czasem, gdy przepływ pracy stanie się bezczynny i jest utrwalany.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-109">A Timespan value that specifies the duration between the time the workflow becomes idle and is persisted.</span></span> <span data-ttu-id="b6dd9-110">Wartość domyślna to TimeSpan. MaxValue.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-110">The default value is TimeSpan.MaxValue.</span></span><br /><br /> <span data-ttu-id="b6dd9-111">Czas trwania rozpoczyna upłynąć, gdy wystąpienie przepływu pracy staje się nieaktywna.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-111">The duration begins to elapse when the workflow instance becomes idle.</span></span> <span data-ttu-id="b6dd9-112">Ten atrybut jest przydatny, jeśli chcesz, aby wystąpienie przepływu pracy było bardziej agresywne i nadal utrzymywać wystąpienie w pamięci tak długo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-112">This attribute  is useful if you want to persist a workflow instance more aggressively while still keeping the instance in memory for as long as possible.</span></span> <span data-ttu-id="b6dd9-113">Ten atrybut jest prawidłowy tylko wtedy, gdy jego wartość jest mniejsza niż atrybut **TimeToUnload** .</span><span class="sxs-lookup"><span data-stu-id="b6dd9-113">This attribute  is only valid if its value is less than the **timeToUnload** attribute.</span></span> <span data-ttu-id="b6dd9-114">Jeśli jest większa, jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-114">If it is greater, it is ignored.</span></span> <span data-ttu-id="b6dd9-115">Jeśli ten atrybut upłynie przed wartością określoną przez atrybut **TimeToUnload** , trwałość musi zostać zakończona przed odładowaniem przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-115">If this attribute elapses before the value specified by the **timeToUnload** attribute, persistence must complete before the workflow is unloaded.</span></span> <span data-ttu-id="b6dd9-116">Oznacza to, że operacja zwolnienia może zostać opóźniona, dopóki przepływ pracy nie zostanie utrwalony.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-116">This implies that the unload operation may be delayed until the workflow is persisted.</span></span> <span data-ttu-id="b6dd9-117">Warstwa trwałości jest odpowiedzialny za obsługę dowolnego powtórzeń przejściowy błędów i tylko na błędy bez nieodwracalny zgłasza wyjątek wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-117">The persistence layer is responsible for handling any retries for transient errors and only throws exceptions on non-recoverable errors.</span></span> <span data-ttu-id="b6dd9-118">Dlatego wyjątki zgłaszane w trwałości są traktowane jako krytyczny, a wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-118">Therefore, any exceptions thrown during persistence are treated as fatal and the workflow instance is aborted.</span></span>|  
|<span data-ttu-id="b6dd9-119">timeToUnload</span><span class="sxs-lookup"><span data-stu-id="b6dd9-119">timeToUnload</span></span>|<span data-ttu-id="b6dd9-120">Zakres czasu wartość, która określa czas trwania między czas przepływu pracy staje się bezczynności i jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-120">A Timespan value that specifies the duration between the time the workflow becomes idle and is unloaded.</span></span> <span data-ttu-id="b6dd9-121">Wartość domyślna to 1 minutę.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-121">The default value is 1 minute.</span></span><br /><br /> <span data-ttu-id="b6dd9-122">Zwalnianie przepływu pracy oznacza, że jest również utrwalone.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-122">Unloading a workflow implies that it is also persisted.</span></span> <span data-ttu-id="b6dd9-123">Jeśli ten atrybut ma wartość zero, wystąpienie przepływu pracy jest utrwalane i zwalniane natychmiast po przejściu przepływu pracy w stan bezczynności.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-123">If this attribute is set to zero the workflow instance is persisted and unloaded immediately after the workflow becomes idle.</span></span> <span data-ttu-id="b6dd9-124">Ustawienie tego atrybutu na TimeSpan. MaxValue skutecznie wyłącza operację Zwolnij.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-124">Setting this attribute to TimeSpan.MaxValue effectively disables the unload operation.</span></span> <span data-ttu-id="b6dd9-125">Wystąpienia przepływu pracy bezczynności nigdy nie są usuwane.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-125">Idle workflow instances are never unloaded.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6dd9-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6dd9-126">Child Elements</span></span>  
 <span data-ttu-id="b6dd9-127">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6dd9-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6dd9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="b6dd9-129">Element</span><span class="sxs-lookup"><span data-stu-id="b6dd9-129">Element</span></span>|<span data-ttu-id="b6dd9-130">Opis</span><span class="sxs-lookup"><span data-stu-id="b6dd9-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6dd9-131">\<behavior>z\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b6dd9-131">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="b6dd9-132">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="b6dd9-132">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6dd9-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6dd9-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>
- <xref:System.ServiceModel.Activities.Configuration.WorkflowIdleElement>
