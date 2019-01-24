---
title: '&lt;Stany&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: d1ec35b1c434b8188fde7b546e2dee42a93f5c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550581"
---
# <a name="ltstatesgt"></a><span data-ttu-id="e7ae8-102">&lt;Stany&gt;</span><span class="sxs-lookup"><span data-stu-id="e7ae8-102">&lt;states&gt;</span></span>
<span data-ttu-id="e7ae8-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="e7ae8-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e7ae8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e7ae8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e7ae8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e7ae8-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e7ae8-106">\<tracking></span></span>  
<span data-ttu-id="e7ae8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e7ae8-107">\<trackingProfile></span></span>  
<span data-ttu-id="e7ae8-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e7ae8-108">\<workflow></span></span>  
<span data-ttu-id="e7ae8-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="e7ae8-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e7ae8-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="e7ae8-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="e7ae8-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="e7ae8-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ae8-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7ae8-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ae8-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7ae8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ae8-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ae8-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7ae8-115">Attributes</span></span>  
 <span data-ttu-id="e7ae8-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7ae8-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ae8-117">Child Elements</span></span>  
  
|<span data-ttu-id="e7ae8-118">Element</span><span class="sxs-lookup"><span data-stu-id="e7ae8-118">Element</span></span>|<span data-ttu-id="e7ae8-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ae8-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ae8-120">\<state></span><span class="sxs-lookup"><span data-stu-id="e7ae8-120">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e7ae8-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ae8-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ae8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ae8-123">Element</span><span class="sxs-lookup"><span data-stu-id="e7ae8-123">Element</span></span>|<span data-ttu-id="e7ae8-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ae8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ae8-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="e7ae8-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="e7ae8-126">Zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7ae8-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e7ae8-127">Remarks</span></span>  
 <span data-ttu-id="e7ae8-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="e7ae8-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="e7ae8-130">Stan</span><span class="sxs-lookup"><span data-stu-id="e7ae8-130">State</span></span>|<span data-ttu-id="e7ae8-131">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ae8-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e7ae8-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="e7ae8-132">Aborted</span></span>|<span data-ttu-id="e7ae8-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="e7ae8-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="e7ae8-134">Completed</span></span>|<span data-ttu-id="e7ae8-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="e7ae8-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="e7ae8-136">Deleted</span></span>|<span data-ttu-id="e7ae8-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="e7ae8-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="e7ae8-138">Idle</span></span>|<span data-ttu-id="e7ae8-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="e7ae8-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="e7ae8-140">Persisted</span></span>|<span data-ttu-id="e7ae8-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="e7ae8-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="e7ae8-142">Resumed</span></span>|<span data-ttu-id="e7ae8-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="e7ae8-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="e7ae8-144">Started</span></span>|<span data-ttu-id="e7ae8-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="e7ae8-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="e7ae8-146">UnhandledException</span></span>|<span data-ttu-id="e7ae8-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="e7ae8-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="e7ae8-148">Unloaded</span></span>|<span data-ttu-id="e7ae8-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="e7ae8-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="e7ae8-150">Canceled</span></span>|<span data-ttu-id="e7ae8-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="e7ae8-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="e7ae8-152">Suspended</span></span>|<span data-ttu-id="e7ae8-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="e7ae8-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="e7ae8-154">Terminated</span></span>|<span data-ttu-id="e7ae8-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="e7ae8-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="e7ae8-156">Unsuspended</span></span>|<span data-ttu-id="e7ae8-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e7ae8-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7ae8-158">Example</span></span>  
 <span data-ttu-id="e7ae8-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e7ae8-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ae8-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7ae8-160">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e7ae8-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e7ae8-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7ae8-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e7ae8-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
