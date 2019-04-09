---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 30cb2efa4c00c8b292a8ace6a03306d6ac76a7f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073125"
---
# <a name="states"></a><span data-ttu-id="18ad0-101">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="18ad0-101">\<states></span></span>
<span data-ttu-id="18ad0-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="18ad0-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="18ad0-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="18ad0-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="18ad0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="18ad0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="18ad0-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="18ad0-105">\<tracking></span></span>  
<span data-ttu-id="18ad0-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="18ad0-106">\<trackingProfile></span></span>  
<span data-ttu-id="18ad0-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="18ad0-107">\<workflow></span></span>  
<span data-ttu-id="18ad0-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="18ad0-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="18ad0-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="18ad0-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="18ad0-110">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="18ad0-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ad0-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="18ad0-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18ad0-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18ad0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="18ad0-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18ad0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18ad0-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18ad0-114">Attributes</span></span>  
 <span data-ttu-id="18ad0-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="18ad0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="18ad0-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18ad0-116">Child Elements</span></span>  
  
|<span data-ttu-id="18ad0-117">Element</span><span class="sxs-lookup"><span data-stu-id="18ad0-117">Element</span></span>|<span data-ttu-id="18ad0-118">Opis</span><span class="sxs-lookup"><span data-stu-id="18ad0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18ad0-119">\<state></span><span class="sxs-lookup"><span data-stu-id="18ad0-119">\<state></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="18ad0-120">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="18ad0-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18ad0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18ad0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="18ad0-122">Element</span><span class="sxs-lookup"><span data-stu-id="18ad0-122">Element</span></span>|<span data-ttu-id="18ad0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="18ad0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18ad0-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="18ad0-124">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="18ad0-125">Zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="18ad0-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ad0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18ad0-126">Remarks</span></span>  
 <span data-ttu-id="18ad0-127">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="18ad0-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="18ad0-128">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="18ad0-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="18ad0-129">Stan</span><span class="sxs-lookup"><span data-stu-id="18ad0-129">State</span></span>|<span data-ttu-id="18ad0-130">Opis</span><span class="sxs-lookup"><span data-stu-id="18ad0-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="18ad0-131">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="18ad0-131">Aborted</span></span>|<span data-ttu-id="18ad0-132">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="18ad0-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="18ad0-133">Zakończone</span><span class="sxs-lookup"><span data-stu-id="18ad0-133">Completed</span></span>|<span data-ttu-id="18ad0-134">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="18ad0-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="18ad0-135">Usunięte</span><span class="sxs-lookup"><span data-stu-id="18ad0-135">Deleted</span></span>|<span data-ttu-id="18ad0-136">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="18ad0-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="18ad0-137">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="18ad0-137">Idle</span></span>|<span data-ttu-id="18ad0-138">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="18ad0-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="18ad0-139">Trwały</span><span class="sxs-lookup"><span data-stu-id="18ad0-139">Persisted</span></span>|<span data-ttu-id="18ad0-140">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="18ad0-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="18ad0-141">Wznowione</span><span class="sxs-lookup"><span data-stu-id="18ad0-141">Resumed</span></span>|<span data-ttu-id="18ad0-142">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="18ad0-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="18ad0-143">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="18ad0-143">Started</span></span>|<span data-ttu-id="18ad0-144">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="18ad0-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="18ad0-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="18ad0-145">UnhandledException</span></span>|<span data-ttu-id="18ad0-146">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="18ad0-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="18ad0-147">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="18ad0-147">Unloaded</span></span>|<span data-ttu-id="18ad0-148">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="18ad0-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="18ad0-149">Anulowane</span><span class="sxs-lookup"><span data-stu-id="18ad0-149">Canceled</span></span>|<span data-ttu-id="18ad0-150">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="18ad0-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="18ad0-151">Suspended</span><span class="sxs-lookup"><span data-stu-id="18ad0-151">Suspended</span></span>|<span data-ttu-id="18ad0-152">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="18ad0-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="18ad0-153">Zakończone</span><span class="sxs-lookup"><span data-stu-id="18ad0-153">Terminated</span></span>|<span data-ttu-id="18ad0-154">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="18ad0-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="18ad0-155">Anulowano</span><span class="sxs-lookup"><span data-stu-id="18ad0-155">Unsuspended</span></span>|<span data-ttu-id="18ad0-156">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="18ad0-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="18ad0-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="18ad0-157">Example</span></span>  
 <span data-ttu-id="18ad0-158">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="18ad0-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18ad0-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18ad0-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="18ad0-160">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="18ad0-160">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="18ad0-161">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="18ad0-161">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
