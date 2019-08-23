---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 9ffe9f9f69f68b6f47cbc3a75200b2867aae2384
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947435"
---
# <a name="state"></a><span data-ttu-id="2c241-101">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="2c241-101">\<state></span></span>
<span data-ttu-id="2c241-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c241-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="2c241-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2c241-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2c241-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2c241-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2c241-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2c241-105">\<tracking></span></span>  
<span data-ttu-id="2c241-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2c241-106">\<trackingProfile></span></span>  
<span data-ttu-id="2c241-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2c241-107">\<workflow></span></span>  
<span data-ttu-id="2c241-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="2c241-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="2c241-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="2c241-109">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="2c241-110">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="2c241-110">\<states></span></span>  
<span data-ttu-id="2c241-111">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="2c241-111">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c241-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c241-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c241-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2c241-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2c241-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2c241-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c241-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2c241-115">Attributes</span></span>  
  
|<span data-ttu-id="2c241-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2c241-116">Attribute</span></span>|<span data-ttu-id="2c241-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2c241-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c241-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="2c241-118">name</span></span>|<span data-ttu-id="2c241-119">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c241-119">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c241-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2c241-120">Child Elements</span></span>  
 <span data-ttu-id="2c241-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="2c241-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c241-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2c241-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2c241-123">Element</span><span class="sxs-lookup"><span data-stu-id="2c241-123">Element</span></span>|<span data-ttu-id="2c241-124">Opis</span><span class="sxs-lookup"><span data-stu-id="2c241-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c241-125">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="2c241-125">\<states></span></span>](states.md)|<span data-ttu-id="2c241-126">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2c241-126">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c241-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c241-127">Remarks</span></span>  
 <span data-ttu-id="2c241-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2c241-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="2c241-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2c241-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="2c241-130">Stan</span><span class="sxs-lookup"><span data-stu-id="2c241-130">State</span></span>|<span data-ttu-id="2c241-131">Opis</span><span class="sxs-lookup"><span data-stu-id="2c241-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c241-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="2c241-132">Aborted</span></span>|<span data-ttu-id="2c241-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="2c241-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2c241-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="2c241-134">Completed</span></span>|<span data-ttu-id="2c241-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="2c241-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="2c241-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="2c241-136">Deleted</span></span>|<span data-ttu-id="2c241-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="2c241-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="2c241-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="2c241-138">Idle</span></span>|<span data-ttu-id="2c241-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="2c241-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="2c241-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="2c241-140">Persisted</span></span>|<span data-ttu-id="2c241-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="2c241-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="2c241-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="2c241-142">Resumed</span></span>|<span data-ttu-id="2c241-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="2c241-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="2c241-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="2c241-144">Started</span></span>|<span data-ttu-id="2c241-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="2c241-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="2c241-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="2c241-146">UnhandledException</span></span>|<span data-ttu-id="2c241-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2c241-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="2c241-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="2c241-148">Unloaded</span></span>|<span data-ttu-id="2c241-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="2c241-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="2c241-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="2c241-150">Canceled</span></span>|<span data-ttu-id="2c241-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="2c241-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="2c241-152">Suspended</span><span class="sxs-lookup"><span data-stu-id="2c241-152">Suspended</span></span>|<span data-ttu-id="2c241-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="2c241-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="2c241-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="2c241-154">Terminated</span></span>|<span data-ttu-id="2c241-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="2c241-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="2c241-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="2c241-156">Unsuspended</span></span>|<span data-ttu-id="2c241-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2c241-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2c241-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="2c241-158">Example</span></span>  
 <span data-ttu-id="2c241-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="2c241-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c241-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c241-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2c241-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2c241-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2c241-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2c241-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
