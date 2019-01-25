---
title: '&lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 8e381671d9282218a4e5bf0ae979bec79c7cfe78
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523054"
---
# <a name="ltstategt"></a><span data-ttu-id="bf181-102">&lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="bf181-102">&lt;state&gt;</span></span>
<span data-ttu-id="bf181-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf181-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="bf181-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bf181-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bf181-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bf181-105">\<system.serviceModel></span></span>  
<span data-ttu-id="bf181-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="bf181-106">\<tracking></span></span>  
<span data-ttu-id="bf181-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bf181-107">\<trackingProfile></span></span>  
<span data-ttu-id="bf181-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="bf181-108">\<workflow></span></span>  
<span data-ttu-id="bf181-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="bf181-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="bf181-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="bf181-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="bf181-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="bf181-111">\<states></span></span>  
<span data-ttu-id="bf181-112">\<state></span><span class="sxs-lookup"><span data-stu-id="bf181-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf181-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf181-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf181-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf181-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bf181-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf181-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf181-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf181-116">Attributes</span></span>  
  
|<span data-ttu-id="bf181-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf181-117">Attribute</span></span>|<span data-ttu-id="bf181-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bf181-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf181-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="bf181-119">name</span></span>|<span data-ttu-id="bf181-120">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf181-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf181-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf181-121">Child Elements</span></span>  
 <span data-ttu-id="bf181-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf181-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf181-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf181-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bf181-124">Element</span><span class="sxs-lookup"><span data-stu-id="bf181-124">Element</span></span>|<span data-ttu-id="bf181-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bf181-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf181-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="bf181-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="bf181-127">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="bf181-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf181-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf181-128">Remarks</span></span>  
 <span data-ttu-id="bf181-129">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="bf181-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="bf181-130">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="bf181-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="bf181-131">Stan</span><span class="sxs-lookup"><span data-stu-id="bf181-131">State</span></span>|<span data-ttu-id="bf181-132">Opis</span><span class="sxs-lookup"><span data-stu-id="bf181-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf181-133">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="bf181-133">Aborted</span></span>|<span data-ttu-id="bf181-134">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="bf181-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="bf181-135">Zakończone</span><span class="sxs-lookup"><span data-stu-id="bf181-135">Completed</span></span>|<span data-ttu-id="bf181-136">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="bf181-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="bf181-137">Usunięte</span><span class="sxs-lookup"><span data-stu-id="bf181-137">Deleted</span></span>|<span data-ttu-id="bf181-138">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="bf181-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="bf181-139">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="bf181-139">Idle</span></span>|<span data-ttu-id="bf181-140">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="bf181-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="bf181-141">Trwały</span><span class="sxs-lookup"><span data-stu-id="bf181-141">Persisted</span></span>|<span data-ttu-id="bf181-142">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="bf181-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="bf181-143">Wznowione</span><span class="sxs-lookup"><span data-stu-id="bf181-143">Resumed</span></span>|<span data-ttu-id="bf181-144">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="bf181-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="bf181-145">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="bf181-145">Started</span></span>|<span data-ttu-id="bf181-146">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="bf181-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="bf181-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="bf181-147">UnhandledException</span></span>|<span data-ttu-id="bf181-148">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="bf181-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="bf181-149">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="bf181-149">Unloaded</span></span>|<span data-ttu-id="bf181-150">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="bf181-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="bf181-151">Anulowane</span><span class="sxs-lookup"><span data-stu-id="bf181-151">Canceled</span></span>|<span data-ttu-id="bf181-152">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="bf181-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="bf181-153">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="bf181-153">Suspended</span></span>|<span data-ttu-id="bf181-154">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="bf181-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="bf181-155">Zakończone</span><span class="sxs-lookup"><span data-stu-id="bf181-155">Terminated</span></span>|<span data-ttu-id="bf181-156">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="bf181-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="bf181-157">Anulowano</span><span class="sxs-lookup"><span data-stu-id="bf181-157">Unsuspended</span></span>|<span data-ttu-id="bf181-158">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf181-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bf181-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf181-159">Example</span></span>  
 <span data-ttu-id="bf181-160">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="bf181-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf181-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf181-161">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bf181-162">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bf181-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bf181-163">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="bf181-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
