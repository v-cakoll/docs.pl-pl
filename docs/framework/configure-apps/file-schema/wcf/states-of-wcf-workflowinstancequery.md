---
title: <states> w WCF — <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281466"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="f134e-102">\<Stany > w WCF — \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="f134e-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="f134e-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f134e-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="f134e-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f134e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f134e-105">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="f134e-105">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="f134e-106">\<profiles></span><span class="sxs-lookup"><span data-stu-id="f134e-106">\<profiles></span></span>  
<span data-ttu-id="f134e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f134e-107">\<trackingProfile></span></span>  
<span data-ttu-id="f134e-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f134e-108">\<workflow></span></span>  
<span data-ttu-id="f134e-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="f134e-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="f134e-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f134e-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="f134e-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="f134e-111">\<states></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f134e-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f134e-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f134e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f134e-113">Attributes and elements</span></span>

<span data-ttu-id="f134e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f134e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f134e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f134e-115">Attributes</span></span>  

<span data-ttu-id="f134e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f134e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f134e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f134e-117">Child elements</span></span>
  
|<span data-ttu-id="f134e-118">Element</span><span class="sxs-lookup"><span data-stu-id="f134e-118">Element</span></span>|<span data-ttu-id="f134e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f134e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f134e-120">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="f134e-120">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="f134e-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f134e-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f134e-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f134e-122">Parent elements</span></span>  
  
|<span data-ttu-id="f134e-123">Element</span><span class="sxs-lookup"><span data-stu-id="f134e-123">Element</span></span>|<span data-ttu-id="f134e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f134e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f134e-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="f134e-125">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="f134e-126">Zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="f134e-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f134e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f134e-127">Remarks</span></span>

<span data-ttu-id="f134e-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f134e-128">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="f134e-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f134e-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="f134e-130">Stan</span><span class="sxs-lookup"><span data-stu-id="f134e-130">State</span></span>|<span data-ttu-id="f134e-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f134e-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f134e-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="f134e-132">Aborted</span></span>|<span data-ttu-id="f134e-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="f134e-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="f134e-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="f134e-134">Completed</span></span>|<span data-ttu-id="f134e-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="f134e-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="f134e-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="f134e-136">Deleted</span></span>|<span data-ttu-id="f134e-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="f134e-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="f134e-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="f134e-138">Idle</span></span>|<span data-ttu-id="f134e-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="f134e-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="f134e-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="f134e-140">Persisted</span></span>|<span data-ttu-id="f134e-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="f134e-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="f134e-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="f134e-142">Resumed</span></span>|<span data-ttu-id="f134e-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="f134e-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="f134e-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="f134e-144">Started</span></span>|<span data-ttu-id="f134e-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="f134e-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="f134e-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="f134e-146">UnhandledException</span></span>|<span data-ttu-id="f134e-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f134e-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="f134e-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="f134e-148">Unloaded</span></span>|<span data-ttu-id="f134e-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="f134e-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="f134e-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="f134e-150">Canceled</span></span>|<span data-ttu-id="f134e-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="f134e-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="f134e-152">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="f134e-152">Suspended</span></span>|<span data-ttu-id="f134e-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f134e-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="f134e-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="f134e-154">Terminated</span></span>|<span data-ttu-id="f134e-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="f134e-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="f134e-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="f134e-156">Unsuspended</span></span>|<span data-ttu-id="f134e-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f134e-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f134e-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="f134e-158">Example</span></span>

<span data-ttu-id="f134e-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="f134e-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="f134e-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f134e-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f134e-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f134e-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f134e-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f134e-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
