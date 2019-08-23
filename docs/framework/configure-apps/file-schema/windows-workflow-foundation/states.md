---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: fd0b57d7d08cf77ba7792e079b7abd2ff8f2839e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947407"
---
# <a name="states"></a><span data-ttu-id="52a6b-101">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="52a6b-101">\<states></span></span>
<span data-ttu-id="52a6b-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="52a6b-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="52a6b-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="52a6b-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="52a6b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="52a6b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="52a6b-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="52a6b-105">\<tracking></span></span>  
<span data-ttu-id="52a6b-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="52a6b-106">\<trackingProfile></span></span>  
<span data-ttu-id="52a6b-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="52a6b-107">\<workflow></span></span>  
<span data-ttu-id="52a6b-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="52a6b-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="52a6b-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="52a6b-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="52a6b-110">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="52a6b-110">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52a6b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="52a6b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52a6b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="52a6b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="52a6b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="52a6b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52a6b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="52a6b-114">Attributes</span></span>  
 <span data-ttu-id="52a6b-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="52a6b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="52a6b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="52a6b-116">Child Elements</span></span>  
  
|<span data-ttu-id="52a6b-117">Element</span><span class="sxs-lookup"><span data-stu-id="52a6b-117">Element</span></span>|<span data-ttu-id="52a6b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="52a6b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52a6b-119">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="52a6b-119">\<state></span></span>](states.md)|<span data-ttu-id="52a6b-120">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="52a6b-120">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52a6b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="52a6b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="52a6b-122">Element</span><span class="sxs-lookup"><span data-stu-id="52a6b-122">Element</span></span>|<span data-ttu-id="52a6b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="52a6b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52a6b-124">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="52a6b-124">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="52a6b-125">Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="52a6b-125">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52a6b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52a6b-126">Remarks</span></span>  
 <span data-ttu-id="52a6b-127">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="52a6b-127">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="52a6b-128">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="52a6b-128">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="52a6b-129">Stan</span><span class="sxs-lookup"><span data-stu-id="52a6b-129">State</span></span>|<span data-ttu-id="52a6b-130">Opis</span><span class="sxs-lookup"><span data-stu-id="52a6b-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="52a6b-131">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="52a6b-131">Aborted</span></span>|<span data-ttu-id="52a6b-132">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="52a6b-132">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="52a6b-133">Zakończone</span><span class="sxs-lookup"><span data-stu-id="52a6b-133">Completed</span></span>|<span data-ttu-id="52a6b-134">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="52a6b-134">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="52a6b-135">Usunięte</span><span class="sxs-lookup"><span data-stu-id="52a6b-135">Deleted</span></span>|<span data-ttu-id="52a6b-136">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="52a6b-136">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="52a6b-137">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="52a6b-137">Idle</span></span>|<span data-ttu-id="52a6b-138">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="52a6b-138">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="52a6b-139">Trwały</span><span class="sxs-lookup"><span data-stu-id="52a6b-139">Persisted</span></span>|<span data-ttu-id="52a6b-140">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="52a6b-140">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="52a6b-141">Wznowione</span><span class="sxs-lookup"><span data-stu-id="52a6b-141">Resumed</span></span>|<span data-ttu-id="52a6b-142">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="52a6b-142">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="52a6b-143">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="52a6b-143">Started</span></span>|<span data-ttu-id="52a6b-144">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="52a6b-144">The workflow instance is started.</span></span>|  
|<span data-ttu-id="52a6b-145">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="52a6b-145">UnhandledException</span></span>|<span data-ttu-id="52a6b-146">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="52a6b-146">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="52a6b-147">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="52a6b-147">Unloaded</span></span>|<span data-ttu-id="52a6b-148">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="52a6b-148">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="52a6b-149">Anulowane</span><span class="sxs-lookup"><span data-stu-id="52a6b-149">Canceled</span></span>|<span data-ttu-id="52a6b-150">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="52a6b-150">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="52a6b-151">Suspended</span><span class="sxs-lookup"><span data-stu-id="52a6b-151">Suspended</span></span>|<span data-ttu-id="52a6b-152">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="52a6b-152">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="52a6b-153">Zakończone</span><span class="sxs-lookup"><span data-stu-id="52a6b-153">Terminated</span></span>|<span data-ttu-id="52a6b-154">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="52a6b-154">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="52a6b-155">Anulowano</span><span class="sxs-lookup"><span data-stu-id="52a6b-155">Unsuspended</span></span>|<span data-ttu-id="52a6b-156">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="52a6b-156">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="52a6b-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="52a6b-157">Example</span></span>  
 <span data-ttu-id="52a6b-158">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="52a6b-158">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="52a6b-159">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52a6b-159">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="52a6b-160">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="52a6b-160">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="52a6b-161">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="52a6b-161">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
