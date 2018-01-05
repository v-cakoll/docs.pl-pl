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
ms.workload: dotnet
ms.openlocfilehash: 5995ebfc2cee0f636d2acd8b1cadead0bc7b67e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="9c566-102">&lt;states&gt; w WCF — &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="9c566-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="9c566-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c566-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="9c566-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9c566-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="9c566-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9c566-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9c566-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9c566-106">\<tracking></span></span>  
<span data-ttu-id="9c566-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="9c566-107">\<trackingProfile></span></span>  
<span data-ttu-id="9c566-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9c566-108">\<workflow></span></span>  
<span data-ttu-id="9c566-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="9c566-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="9c566-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="9c566-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="9c566-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="9c566-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c566-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c566-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c566-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9c566-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9c566-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9c566-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c566-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9c566-115">Attributes</span></span>  
 <span data-ttu-id="9c566-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="9c566-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9c566-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9c566-117">Child Elements</span></span>  
  
|<span data-ttu-id="9c566-118">Element</span><span class="sxs-lookup"><span data-stu-id="9c566-118">Element</span></span>|<span data-ttu-id="9c566-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9c566-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c566-120">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="9c566-120">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="9c566-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c566-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9c566-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9c566-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9c566-123">Element</span><span class="sxs-lookup"><span data-stu-id="9c566-123">Element</span></span>|<span data-ttu-id="9c566-124">Opis</span><span class="sxs-lookup"><span data-stu-id="9c566-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c566-125">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="9c566-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="9c566-126">Kwerenda, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="9c566-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c566-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c566-127">Remarks</span></span>  
 <span data-ttu-id="9c566-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9c566-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="9c566-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9c566-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="9c566-130">Stan</span><span class="sxs-lookup"><span data-stu-id="9c566-130">State</span></span>|<span data-ttu-id="9c566-131">Opis</span><span class="sxs-lookup"><span data-stu-id="9c566-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9c566-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="9c566-132">Aborted</span></span>|<span data-ttu-id="9c566-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="9c566-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="9c566-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="9c566-134">Completed</span></span>|<span data-ttu-id="9c566-135">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="9c566-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="9c566-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="9c566-136">Deleted</span></span>|<span data-ttu-id="9c566-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="9c566-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="9c566-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="9c566-138">Idle</span></span>|<span data-ttu-id="9c566-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="9c566-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="9c566-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="9c566-140">Persisted</span></span>|<span data-ttu-id="9c566-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="9c566-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="9c566-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="9c566-142">Resumed</span></span>|<span data-ttu-id="9c566-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="9c566-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="9c566-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="9c566-144">Started</span></span>|<span data-ttu-id="9c566-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="9c566-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="9c566-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="9c566-146">UnhandledException</span></span>|<span data-ttu-id="9c566-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9c566-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="9c566-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="9c566-148">Unloaded</span></span>|<span data-ttu-id="9c566-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="9c566-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="9c566-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="9c566-150">Canceled</span></span>|<span data-ttu-id="9c566-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="9c566-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="9c566-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="9c566-152">Suspended</span></span>|<span data-ttu-id="9c566-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="9c566-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="9c566-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="9c566-154">Terminated</span></span>|<span data-ttu-id="9c566-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="9c566-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="9c566-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="9c566-156">Unsuspended</span></span>|<span data-ttu-id="9c566-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9c566-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c566-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c566-158">Example</span></span>  
 <span data-ttu-id="9c566-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="9c566-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c566-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c566-160">See Also</span></span>  
 <span data-ttu-id="9c566-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9c566-161"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9c566-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9c566-162"><xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="9c566-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9c566-163"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="9c566-164">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9c566-164">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9c566-165">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9c566-165">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
