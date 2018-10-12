---
title: '&lt;states&gt; w WCF — &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: a6c54f0903f30b5a7c3147cf4b874516a766c2b8
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121947"
---
# <a name="ltstatesgt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="7d6c4-102">&lt;states&gt; w WCF — &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="7d6c4-102">&lt;states&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>

<span data-ttu-id="7d6c4-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="7d6c4-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7d6c4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7d6c4-105">\<system.serviceModel > \<śledzenia ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="7d6c4-106">\<profile ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-106">\<profiles></span></span>  
<span data-ttu-id="7d6c4-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7d6c4-107">\<trackingProfile></span></span>  
<span data-ttu-id="7d6c4-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-108">\<workflow></span></span>  
<span data-ttu-id="7d6c4-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="7d6c4-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="7d6c4-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="7d6c4-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d6c4-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d6c4-112">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d6c4-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d6c4-113">Attributes and elements</span></span>

<span data-ttu-id="7d6c4-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d6c4-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d6c4-115">Attributes</span></span>  

<span data-ttu-id="7d6c4-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d6c4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d6c4-117">Child elements</span></span>
  
|<span data-ttu-id="7d6c4-118">Element</span><span class="sxs-lookup"><span data-stu-id="7d6c4-118">Element</span></span>|<span data-ttu-id="7d6c4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7d6c4-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d6c4-120">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="7d6c4-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="7d6c4-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d6c4-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d6c4-122">Parent elements</span></span>  
  
|<span data-ttu-id="7d6c4-123">Element</span><span class="sxs-lookup"><span data-stu-id="7d6c4-123">Element</span></span>|<span data-ttu-id="7d6c4-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7d6c4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d6c4-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="7d6c4-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="7d6c4-126">Zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d6c4-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d6c4-127">Remarks</span></span>

<span data-ttu-id="7d6c4-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="7d6c4-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="7d6c4-130">Stan</span><span class="sxs-lookup"><span data-stu-id="7d6c4-130">State</span></span>|<span data-ttu-id="7d6c4-131">Opis</span><span class="sxs-lookup"><span data-stu-id="7d6c4-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7d6c4-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="7d6c4-132">Aborted</span></span>|<span data-ttu-id="7d6c4-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="7d6c4-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="7d6c4-134">Completed</span></span>|<span data-ttu-id="7d6c4-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="7d6c4-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="7d6c4-136">Deleted</span></span>|<span data-ttu-id="7d6c4-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="7d6c4-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="7d6c4-138">Idle</span></span>|<span data-ttu-id="7d6c4-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="7d6c4-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="7d6c4-140">Persisted</span></span>|<span data-ttu-id="7d6c4-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="7d6c4-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="7d6c4-142">Resumed</span></span>|<span data-ttu-id="7d6c4-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="7d6c4-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="7d6c4-144">Started</span></span>|<span data-ttu-id="7d6c4-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="7d6c4-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="7d6c4-146">UnhandledException</span></span>|<span data-ttu-id="7d6c4-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="7d6c4-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="7d6c4-148">Unloaded</span></span>|<span data-ttu-id="7d6c4-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="7d6c4-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="7d6c4-150">Canceled</span></span>|<span data-ttu-id="7d6c4-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="7d6c4-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="7d6c4-152">Suspended</span></span>|<span data-ttu-id="7d6c4-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="7d6c4-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="7d6c4-154">Terminated</span></span>|<span data-ttu-id="7d6c4-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="7d6c4-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="7d6c4-156">Unsuspended</span></span>|<span data-ttu-id="7d6c4-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d6c4-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d6c4-158">Example</span></span>

<span data-ttu-id="7d6c4-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="7d6c4-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d6c4-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d6c4-160">See also</span></span>  

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="7d6c4-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7d6c4-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="7d6c4-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7d6c4-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
