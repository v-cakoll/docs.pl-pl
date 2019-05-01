---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 6f1a9474f3f12005df364a6fb84dc63aa1b68e04
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796165"
---
# <a name="state"></a><span data-ttu-id="14229-101">\<state></span><span class="sxs-lookup"><span data-stu-id="14229-101">\<state></span></span>
<span data-ttu-id="14229-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="14229-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="14229-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="14229-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="14229-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="14229-104">\<system.serviceModel></span></span>  
<span data-ttu-id="14229-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="14229-105">\<tracking></span></span>  
<span data-ttu-id="14229-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="14229-106">\<trackingProfile></span></span>  
<span data-ttu-id="14229-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="14229-107">\<workflow></span></span>  
<span data-ttu-id="14229-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="14229-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="14229-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="14229-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="14229-110">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="14229-110">\<states></span></span>  
<span data-ttu-id="14229-111">\<state></span><span class="sxs-lookup"><span data-stu-id="14229-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14229-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="14229-112">Syntax</span></span>  
  
```xml  
<tracking>
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
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14229-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="14229-113">Attributes and Elements</span></span>  
 <span data-ttu-id="14229-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="14229-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14229-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="14229-115">Attributes</span></span>  
  
|<span data-ttu-id="14229-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="14229-116">Attribute</span></span>|<span data-ttu-id="14229-117">Opis</span><span class="sxs-lookup"><span data-stu-id="14229-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="14229-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="14229-118">name</span></span>|<span data-ttu-id="14229-119">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="14229-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14229-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14229-120">Child Elements</span></span>  
 <span data-ttu-id="14229-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="14229-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14229-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14229-122">Parent Elements</span></span>  
  
|<span data-ttu-id="14229-123">Element</span><span class="sxs-lookup"><span data-stu-id="14229-123">Element</span></span>|<span data-ttu-id="14229-124">Opis</span><span class="sxs-lookup"><span data-stu-id="14229-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14229-125">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="14229-125">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="14229-126">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="14229-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14229-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14229-127">Remarks</span></span>  
 <span data-ttu-id="14229-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="14229-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="14229-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="14229-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="14229-130">Stan</span><span class="sxs-lookup"><span data-stu-id="14229-130">State</span></span>|<span data-ttu-id="14229-131">Opis</span><span class="sxs-lookup"><span data-stu-id="14229-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="14229-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="14229-132">Aborted</span></span>|<span data-ttu-id="14229-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="14229-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="14229-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="14229-134">Completed</span></span>|<span data-ttu-id="14229-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="14229-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="14229-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="14229-136">Deleted</span></span>|<span data-ttu-id="14229-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="14229-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="14229-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="14229-138">Idle</span></span>|<span data-ttu-id="14229-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="14229-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="14229-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="14229-140">Persisted</span></span>|<span data-ttu-id="14229-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="14229-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="14229-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="14229-142">Resumed</span></span>|<span data-ttu-id="14229-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="14229-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="14229-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="14229-144">Started</span></span>|<span data-ttu-id="14229-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="14229-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="14229-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="14229-146">UnhandledException</span></span>|<span data-ttu-id="14229-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="14229-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="14229-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="14229-148">Unloaded</span></span>|<span data-ttu-id="14229-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="14229-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="14229-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="14229-150">Canceled</span></span>|<span data-ttu-id="14229-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="14229-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="14229-152">Suspended</span><span class="sxs-lookup"><span data-stu-id="14229-152">Suspended</span></span>|<span data-ttu-id="14229-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="14229-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="14229-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="14229-154">Terminated</span></span>|<span data-ttu-id="14229-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="14229-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="14229-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="14229-156">Unsuspended</span></span>|<span data-ttu-id="14229-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="14229-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="14229-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="14229-158">Example</span></span>  
 <span data-ttu-id="14229-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="14229-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="14229-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14229-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="14229-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="14229-161">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="14229-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="14229-162">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
