---
title: "&lt;states&gt; w WCF — &lt;workflowInstanceQuery&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65573b72c91eab41bd3167552ff1f42552f40f6b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="262e8-102">&lt;states&gt; w WCF — &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="262e8-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="262e8-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="262e8-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="262e8-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="262e8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="262e8-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="262e8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="262e8-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="262e8-106">\<tracking></span></span>  
<span data-ttu-id="262e8-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="262e8-107">\<trackingProfile></span></span>  
<span data-ttu-id="262e8-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="262e8-108">\<workflow></span></span>  
<span data-ttu-id="262e8-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="262e8-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="262e8-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="262e8-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="262e8-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="262e8-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262e8-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="262e8-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="262e8-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="262e8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="262e8-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="262e8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="262e8-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="262e8-115">Attributes</span></span>  
 <span data-ttu-id="262e8-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="262e8-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="262e8-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="262e8-117">Child Elements</span></span>  
  
|<span data-ttu-id="262e8-118">Element</span><span class="sxs-lookup"><span data-stu-id="262e8-118">Element</span></span>|<span data-ttu-id="262e8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="262e8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="262e8-120">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="262e8-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="262e8-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="262e8-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="262e8-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="262e8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="262e8-123">Element</span><span class="sxs-lookup"><span data-stu-id="262e8-123">Element</span></span>|<span data-ttu-id="262e8-124">Opis</span><span class="sxs-lookup"><span data-stu-id="262e8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="262e8-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="262e8-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="262e8-126">Kwerenda, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="262e8-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="262e8-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="262e8-127">Remarks</span></span>  
 <span data-ttu-id="262e8-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="262e8-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="262e8-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="262e8-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="262e8-130">Stan</span><span class="sxs-lookup"><span data-stu-id="262e8-130">State</span></span>|<span data-ttu-id="262e8-131">Opis</span><span class="sxs-lookup"><span data-stu-id="262e8-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="262e8-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="262e8-132">Aborted</span></span>|<span data-ttu-id="262e8-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="262e8-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="262e8-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="262e8-134">Completed</span></span>|<span data-ttu-id="262e8-135">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="262e8-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="262e8-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="262e8-136">Deleted</span></span>|<span data-ttu-id="262e8-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="262e8-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="262e8-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="262e8-138">Idle</span></span>|<span data-ttu-id="262e8-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="262e8-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="262e8-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="262e8-140">Persisted</span></span>|<span data-ttu-id="262e8-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="262e8-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="262e8-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="262e8-142">Resumed</span></span>|<span data-ttu-id="262e8-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="262e8-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="262e8-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="262e8-144">Started</span></span>|<span data-ttu-id="262e8-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="262e8-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="262e8-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="262e8-146">UnhandledException</span></span>|<span data-ttu-id="262e8-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="262e8-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="262e8-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="262e8-148">Unloaded</span></span>|<span data-ttu-id="262e8-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="262e8-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="262e8-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="262e8-150">Canceled</span></span>|<span data-ttu-id="262e8-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="262e8-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="262e8-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="262e8-152">Suspended</span></span>|<span data-ttu-id="262e8-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="262e8-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="262e8-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="262e8-154">Terminated</span></span>|<span data-ttu-id="262e8-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="262e8-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="262e8-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="262e8-156">Unsuspended</span></span>|<span data-ttu-id="262e8-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="262e8-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="262e8-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="262e8-158">Example</span></span>  
 <span data-ttu-id="262e8-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="262e8-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="262e8-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="262e8-160">See Also</span></span>  
 <span data-ttu-id="262e8-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="262e8-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="262e8-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="262e8-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="262e8-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="262e8-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="262e8-164">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="262e8-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="262e8-165">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="262e8-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
