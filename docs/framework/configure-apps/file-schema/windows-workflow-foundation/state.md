---
title: '&lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 327a5e98a9ecf6ba23eaf47c3d6d73bfb7852ee7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757492"
---
# <a name="ltstategt"></a><span data-ttu-id="2825e-102">&lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="2825e-102">&lt;state&gt;</span></span>
<span data-ttu-id="2825e-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2825e-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="2825e-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2825e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="2825e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2825e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="2825e-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2825e-106">\<tracking></span></span>  
<span data-ttu-id="2825e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2825e-107">\<trackingProfile></span></span>  
<span data-ttu-id="2825e-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2825e-108">\<workflow></span></span>  
<span data-ttu-id="2825e-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="2825e-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="2825e-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="2825e-110">\<workflowInstanceQuery></span></span>  
<span data-ttu-id="2825e-111">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="2825e-111">\<states></span></span>  
<span data-ttu-id="2825e-112">\<Stan ></span><span class="sxs-lookup"><span data-stu-id="2825e-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2825e-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="2825e-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2825e-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2825e-114">Attributes and Elements</span></span>  
 <span data-ttu-id="2825e-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2825e-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2825e-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2825e-116">Attributes</span></span>  
  
|<span data-ttu-id="2825e-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2825e-117">Attribute</span></span>|<span data-ttu-id="2825e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="2825e-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2825e-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="2825e-119">name</span></span>|<span data-ttu-id="2825e-120">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2825e-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2825e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2825e-121">Child Elements</span></span>  
 <span data-ttu-id="2825e-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="2825e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2825e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2825e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2825e-124">Element</span><span class="sxs-lookup"><span data-stu-id="2825e-124">Element</span></span>|<span data-ttu-id="2825e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="2825e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2825e-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="2825e-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="2825e-127">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2825e-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2825e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2825e-128">Remarks</span></span>  
 <span data-ttu-id="2825e-129">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2825e-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="2825e-130">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2825e-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="2825e-131">Stan</span><span class="sxs-lookup"><span data-stu-id="2825e-131">State</span></span>|<span data-ttu-id="2825e-132">Opis</span><span class="sxs-lookup"><span data-stu-id="2825e-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2825e-133">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="2825e-133">Aborted</span></span>|<span data-ttu-id="2825e-134">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="2825e-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2825e-135">Zakończone</span><span class="sxs-lookup"><span data-stu-id="2825e-135">Completed</span></span>|<span data-ttu-id="2825e-136">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="2825e-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="2825e-137">Usunięte</span><span class="sxs-lookup"><span data-stu-id="2825e-137">Deleted</span></span>|<span data-ttu-id="2825e-138">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="2825e-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="2825e-139">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="2825e-139">Idle</span></span>|<span data-ttu-id="2825e-140">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="2825e-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="2825e-141">Trwały</span><span class="sxs-lookup"><span data-stu-id="2825e-141">Persisted</span></span>|<span data-ttu-id="2825e-142">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="2825e-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="2825e-143">Wznowione</span><span class="sxs-lookup"><span data-stu-id="2825e-143">Resumed</span></span>|<span data-ttu-id="2825e-144">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="2825e-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="2825e-145">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="2825e-145">Started</span></span>|<span data-ttu-id="2825e-146">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="2825e-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="2825e-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="2825e-147">UnhandledException</span></span>|<span data-ttu-id="2825e-148">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2825e-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="2825e-149">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="2825e-149">Unloaded</span></span>|<span data-ttu-id="2825e-150">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="2825e-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="2825e-151">Anulowane</span><span class="sxs-lookup"><span data-stu-id="2825e-151">Canceled</span></span>|<span data-ttu-id="2825e-152">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="2825e-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="2825e-153">Wstrzymane</span><span class="sxs-lookup"><span data-stu-id="2825e-153">Suspended</span></span>|<span data-ttu-id="2825e-154">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="2825e-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="2825e-155">Zakończone</span><span class="sxs-lookup"><span data-stu-id="2825e-155">Terminated</span></span>|<span data-ttu-id="2825e-156">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="2825e-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="2825e-157">Anulowano</span><span class="sxs-lookup"><span data-stu-id="2825e-157">Unsuspended</span></span>|<span data-ttu-id="2825e-158">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2825e-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2825e-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="2825e-159">Example</span></span>  
 <span data-ttu-id="2825e-160">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="2825e-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2825e-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2825e-161">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>      
 [<span data-ttu-id="2825e-162">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2825e-162">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2825e-163">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2825e-163">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
