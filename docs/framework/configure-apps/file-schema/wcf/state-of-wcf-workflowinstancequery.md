---
title: '&lt;state&gt; w WCF — &lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 427cba7a51bfb908171e476cd703c6a40fd6e144
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123218"
---
# <a name="ltstategt-of-wcf-ltworkflowinstancequerygt"></a><span data-ttu-id="a349c-102">&lt;state&gt; w WCF — &lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="a349c-102">&lt;state&gt; of WCF, &lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="a349c-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a349c-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="a349c-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a349c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a349c-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a349c-105">\<system.serviceModel></span></span>  
<span data-ttu-id="a349c-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a349c-106">\<tracking></span></span>  
<span data-ttu-id="a349c-107">\<profile ></span><span class="sxs-lookup"><span data-stu-id="a349c-107">\<profiles></span></span>  
<span data-ttu-id="a349c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a349c-108">\<trackingProfile></span></span>  
<span data-ttu-id="a349c-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a349c-109">\<workflow></span></span>  
<span data-ttu-id="a349c-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="a349c-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="a349c-111">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="a349c-111">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="a349c-112">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="a349c-112">\<states></span></span>  
<span data-ttu-id="a349c-113">\<Stan ></span><span class="sxs-lookup"><span data-stu-id="a349c-113">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a349c-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="a349c-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a349c-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a349c-115">Attributes and elements</span></span>

<span data-ttu-id="a349c-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a349c-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="a349c-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a349c-117">Attributes</span></span>

|<span data-ttu-id="a349c-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a349c-118">Attribute</span></span>|<span data-ttu-id="a349c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="a349c-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="a349c-120">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a349c-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a349c-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a349c-121">Child elements</span></span>

<span data-ttu-id="a349c-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="a349c-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a349c-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a349c-123">Parent elements</span></span>

|<span data-ttu-id="a349c-124">Element</span><span class="sxs-lookup"><span data-stu-id="a349c-124">Element</span></span>|<span data-ttu-id="a349c-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a349c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a349c-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="a349c-126">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="a349c-127">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a349c-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a349c-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a349c-128">Remarks</span></span>  

<span data-ttu-id="a349c-129">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a349c-129">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="a349c-130">Stan możliwe wartości są opisane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="a349c-130">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="a349c-131">Stan</span><span class="sxs-lookup"><span data-stu-id="a349c-131">State</span></span>|<span data-ttu-id="a349c-132">Opis</span><span class="sxs-lookup"><span data-stu-id="a349c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a349c-133">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="a349c-133">Aborted</span></span>|<span data-ttu-id="a349c-134">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="a349c-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="a349c-135">Zakończone</span><span class="sxs-lookup"><span data-stu-id="a349c-135">Completed</span></span>|<span data-ttu-id="a349c-136">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="a349c-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="a349c-137">Usunięte</span><span class="sxs-lookup"><span data-stu-id="a349c-137">Deleted</span></span>|<span data-ttu-id="a349c-138">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="a349c-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="a349c-139">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="a349c-139">Idle</span></span>|<span data-ttu-id="a349c-140">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="a349c-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a349c-141">Trwały</span><span class="sxs-lookup"><span data-stu-id="a349c-141">Persisted</span></span>|<span data-ttu-id="a349c-142">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="a349c-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="a349c-143">Wznowione</span><span class="sxs-lookup"><span data-stu-id="a349c-143">Resumed</span></span>|<span data-ttu-id="a349c-144">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="a349c-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="a349c-145">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="a349c-145">Started</span></span>|<span data-ttu-id="a349c-146">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="a349c-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="a349c-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="a349c-147">UnhandledException</span></span>|<span data-ttu-id="a349c-148">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a349c-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="a349c-149">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="a349c-149">Unloaded</span></span>|<span data-ttu-id="a349c-150">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="a349c-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="a349c-151">Anulowane</span><span class="sxs-lookup"><span data-stu-id="a349c-151">Canceled</span></span>|<span data-ttu-id="a349c-152">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="a349c-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="a349c-153">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="a349c-153">Suspended</span></span>|<span data-ttu-id="a349c-154">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="a349c-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="a349c-155">Zakończone</span><span class="sxs-lookup"><span data-stu-id="a349c-155">Terminated</span></span>|<span data-ttu-id="a349c-156">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="a349c-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="a349c-157">Anulowano</span><span class="sxs-lookup"><span data-stu-id="a349c-157">Unsuspended</span></span>|<span data-ttu-id="a349c-158">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a349c-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a349c-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="a349c-159">Example</span></span>

<span data-ttu-id="a349c-160">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="a349c-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml
<workflowInstanceQueries>
  <workflowInstanceQuery>  
    <states>  
      <state name="Started"/>  
    </states>  
  </workflowInstanceQuery>  
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="a349c-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a349c-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a349c-162">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a349c-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a349c-163">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a349c-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
