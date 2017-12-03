---
title: '&lt;Stany&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5e9050a01cf58c3c103fdbe4e8b22e173efaf5c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltstatesgt"></a><span data-ttu-id="a4cb5-102">&lt;Stany&gt;</span><span class="sxs-lookup"><span data-stu-id="a4cb5-102">&lt;states&gt;</span></span>
<span data-ttu-id="a4cb5-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="a4cb5-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a4cb5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a4cb5-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a4cb5-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-106">\<tracking></span></span>  
<span data-ttu-id="a4cb5-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-107">\<trackingProfile></span></span>  
<span data-ttu-id="a4cb5-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-108">\<workflow></span></span>  
<span data-ttu-id="a4cb5-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="a4cb5-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="a4cb5-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4cb5-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4cb5-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="Name"/>
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4cb5-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a4cb5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a4cb5-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4cb5-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a4cb5-115">Attributes</span></span>  
 <span data-ttu-id="a4cb5-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a4cb5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a4cb5-117">Child Elements</span></span>  
  
|<span data-ttu-id="a4cb5-118">Element</span><span class="sxs-lookup"><span data-stu-id="a4cb5-118">Element</span></span>|<span data-ttu-id="a4cb5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a4cb5-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4cb5-120">\<Stan ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="a4cb5-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4cb5-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a4cb5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a4cb5-123">Element</span><span class="sxs-lookup"><span data-stu-id="a4cb5-123">Element</span></span>|<span data-ttu-id="a4cb5-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a4cb5-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4cb5-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="a4cb5-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="a4cb5-126">Kwerenda, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4cb5-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4cb5-127">Remarks</span></span>  
 <span data-ttu-id="a4cb5-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="a4cb5-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="a4cb5-130">Stan</span><span class="sxs-lookup"><span data-stu-id="a4cb5-130">State</span></span>|<span data-ttu-id="a4cb5-131">Opis</span><span class="sxs-lookup"><span data-stu-id="a4cb5-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4cb5-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="a4cb5-132">Aborted</span></span>|<span data-ttu-id="a4cb5-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a4cb5-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="a4cb5-134">Completed</span></span>|<span data-ttu-id="a4cb5-135">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a4cb5-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="a4cb5-136">Deleted</span></span>|<span data-ttu-id="a4cb5-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a4cb5-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="a4cb5-138">Idle</span></span>|<span data-ttu-id="a4cb5-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a4cb5-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="a4cb5-140">Persisted</span></span>|<span data-ttu-id="a4cb5-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a4cb5-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="a4cb5-142">Resumed</span></span>|<span data-ttu-id="a4cb5-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a4cb5-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="a4cb5-144">Started</span></span>|<span data-ttu-id="a4cb5-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a4cb5-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a4cb5-146">UnhandledException</span></span>|<span data-ttu-id="a4cb5-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a4cb5-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="a4cb5-148">Unloaded</span></span>|<span data-ttu-id="a4cb5-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a4cb5-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="a4cb5-150">Canceled</span></span>|<span data-ttu-id="a4cb5-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a4cb5-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="a4cb5-152">Suspended</span></span>|<span data-ttu-id="a4cb5-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a4cb5-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="a4cb5-154">Terminated</span></span>|<span data-ttu-id="a4cb5-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a4cb5-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="a4cb5-156">Unsuspended</span></span>|<span data-ttu-id="a4cb5-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4cb5-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4cb5-158">Example</span></span>  
 <span data-ttu-id="a4cb5-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="a4cb5-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4cb5-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a4cb5-160">See Also</span></span>  
 <span data-ttu-id="a4cb5-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a4cb5-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a4cb5-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a4cb5-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="a4cb5-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="a4cb5-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="a4cb5-164">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="a4cb5-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a4cb5-165">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a4cb5-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
