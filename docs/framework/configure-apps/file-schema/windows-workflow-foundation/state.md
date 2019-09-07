---
title: <state>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 619414f2-61c2-4427-9977-d05009e343db
ms.openlocfilehash: 7af75182cf38a6acb8a31b71e8b7b42103f8046b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398636"
---
# <a name="state"></a><span data-ttu-id="95d05-101">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="95d05-101">\<state></span></span>
<span data-ttu-id="95d05-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95d05-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="95d05-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="95d05-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95d05-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="95d05-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="95d05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="95d05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="95d05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="95d05-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="95d05-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Stany >** ](states.md)</span><span class="sxs-lookup"><span data-stu-id="95d05-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states.md)</span></span>\
<span data-ttu-id="95d05-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> stanu**</span><span class="sxs-lookup"><span data-stu-id="95d05-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d05-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="95d05-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d05-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95d05-114">Attributes and Elements</span></span>  
 <span data-ttu-id="95d05-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95d05-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d05-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95d05-116">Attributes</span></span>  
  
|<span data-ttu-id="95d05-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95d05-117">Attribute</span></span>|<span data-ttu-id="95d05-118">Opis</span><span class="sxs-lookup"><span data-stu-id="95d05-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95d05-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="95d05-119">name</span></span>|<span data-ttu-id="95d05-120">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95d05-120">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95d05-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95d05-121">Child Elements</span></span>  
 <span data-ttu-id="95d05-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="95d05-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95d05-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95d05-123">Parent Elements</span></span>  
  
|<span data-ttu-id="95d05-124">Element</span><span class="sxs-lookup"><span data-stu-id="95d05-124">Element</span></span>|<span data-ttu-id="95d05-125">Opis</span><span class="sxs-lookup"><span data-stu-id="95d05-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d05-126">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="95d05-126">\<states></span></span>](states.md)|<span data-ttu-id="95d05-127">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="95d05-127">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d05-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95d05-128">Remarks</span></span>  
 <span data-ttu-id="95d05-129">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95d05-129">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="95d05-130">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="95d05-130">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="95d05-131">Stan</span><span class="sxs-lookup"><span data-stu-id="95d05-131">State</span></span>|<span data-ttu-id="95d05-132">Opis</span><span class="sxs-lookup"><span data-stu-id="95d05-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="95d05-133">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="95d05-133">Aborted</span></span>|<span data-ttu-id="95d05-134">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="95d05-134">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="95d05-135">Zakończone</span><span class="sxs-lookup"><span data-stu-id="95d05-135">Completed</span></span>|<span data-ttu-id="95d05-136">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="95d05-136">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="95d05-137">Usunięte</span><span class="sxs-lookup"><span data-stu-id="95d05-137">Deleted</span></span>|<span data-ttu-id="95d05-138">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="95d05-138">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="95d05-139">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="95d05-139">Idle</span></span>|<span data-ttu-id="95d05-140">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="95d05-140">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="95d05-141">Trwały</span><span class="sxs-lookup"><span data-stu-id="95d05-141">Persisted</span></span>|<span data-ttu-id="95d05-142">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="95d05-142">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="95d05-143">Wznowione</span><span class="sxs-lookup"><span data-stu-id="95d05-143">Resumed</span></span>|<span data-ttu-id="95d05-144">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="95d05-144">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="95d05-145">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="95d05-145">Started</span></span>|<span data-ttu-id="95d05-146">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="95d05-146">The workflow instance is started.</span></span>|  
|<span data-ttu-id="95d05-147">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="95d05-147">UnhandledException</span></span>|<span data-ttu-id="95d05-148">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="95d05-148">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="95d05-149">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="95d05-149">Unloaded</span></span>|<span data-ttu-id="95d05-150">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="95d05-150">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="95d05-151">Anulowane</span><span class="sxs-lookup"><span data-stu-id="95d05-151">Canceled</span></span>|<span data-ttu-id="95d05-152">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="95d05-152">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="95d05-153">Suspended</span><span class="sxs-lookup"><span data-stu-id="95d05-153">Suspended</span></span>|<span data-ttu-id="95d05-154">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="95d05-154">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="95d05-155">Zakończone</span><span class="sxs-lookup"><span data-stu-id="95d05-155">Terminated</span></span>|<span data-ttu-id="95d05-156">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="95d05-156">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="95d05-157">Anulowano</span><span class="sxs-lookup"><span data-stu-id="95d05-157">Unsuspended</span></span>|<span data-ttu-id="95d05-158">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="95d05-158">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95d05-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="95d05-159">Example</span></span>  
 <span data-ttu-id="95d05-160">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="95d05-160">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95d05-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95d05-161">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="95d05-162">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="95d05-162">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="95d05-163">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="95d05-163">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
