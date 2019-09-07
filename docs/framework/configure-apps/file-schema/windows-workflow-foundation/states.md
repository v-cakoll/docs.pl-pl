---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398618"
---
# <a name="states"></a><span data-ttu-id="c516f-101">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="c516f-101">\<states></span></span>
<span data-ttu-id="c516f-102">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c516f-102">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="c516f-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c516f-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c516f-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c516f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="c516f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="c516f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="c516f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)</span></span>\
<span data-ttu-id="c516f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="c516f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)</span></span>\
<span data-ttu-id="c516f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Stany >**</span><span class="sxs-lookup"><span data-stu-id="c516f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c516f-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="c516f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c516f-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c516f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c516f-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c516f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c516f-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c516f-115">Attributes</span></span>  
 <span data-ttu-id="c516f-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="c516f-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c516f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c516f-117">Child Elements</span></span>  
  
|<span data-ttu-id="c516f-118">Element</span><span class="sxs-lookup"><span data-stu-id="c516f-118">Element</span></span>|<span data-ttu-id="c516f-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c516f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c516f-120">\<> stanu</span><span class="sxs-lookup"><span data-stu-id="c516f-120">\<state></span></span>](states.md)|<span data-ttu-id="c516f-121">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c516f-121">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c516f-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c516f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c516f-123">Element</span><span class="sxs-lookup"><span data-stu-id="c516f-123">Element</span></span>|<span data-ttu-id="c516f-124">Opis</span><span class="sxs-lookup"><span data-stu-id="c516f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c516f-125">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="c516f-125">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="c516f-126">Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="c516f-126">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c516f-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c516f-127">Remarks</span></span>  
 <span data-ttu-id="c516f-128">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c516f-128">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="c516f-129">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c516f-129">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="c516f-130">Stan</span><span class="sxs-lookup"><span data-stu-id="c516f-130">State</span></span>|<span data-ttu-id="c516f-131">Opis</span><span class="sxs-lookup"><span data-stu-id="c516f-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c516f-132">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="c516f-132">Aborted</span></span>|<span data-ttu-id="c516f-133">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="c516f-133">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="c516f-134">Zakończone</span><span class="sxs-lookup"><span data-stu-id="c516f-134">Completed</span></span>|<span data-ttu-id="c516f-135">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="c516f-135">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="c516f-136">Usunięte</span><span class="sxs-lookup"><span data-stu-id="c516f-136">Deleted</span></span>|<span data-ttu-id="c516f-137">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="c516f-137">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="c516f-138">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="c516f-138">Idle</span></span>|<span data-ttu-id="c516f-139">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="c516f-139">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="c516f-140">Trwały</span><span class="sxs-lookup"><span data-stu-id="c516f-140">Persisted</span></span>|<span data-ttu-id="c516f-141">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="c516f-141">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="c516f-142">Wznowione</span><span class="sxs-lookup"><span data-stu-id="c516f-142">Resumed</span></span>|<span data-ttu-id="c516f-143">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="c516f-143">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="c516f-144">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="c516f-144">Started</span></span>|<span data-ttu-id="c516f-145">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="c516f-145">The workflow instance is started.</span></span>|  
|<span data-ttu-id="c516f-146">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="c516f-146">UnhandledException</span></span>|<span data-ttu-id="c516f-147">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c516f-147">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="c516f-148">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="c516f-148">Unloaded</span></span>|<span data-ttu-id="c516f-149">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="c516f-149">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="c516f-150">Anulowane</span><span class="sxs-lookup"><span data-stu-id="c516f-150">Canceled</span></span>|<span data-ttu-id="c516f-151">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="c516f-151">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="c516f-152">Suspended</span><span class="sxs-lookup"><span data-stu-id="c516f-152">Suspended</span></span>|<span data-ttu-id="c516f-153">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="c516f-153">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="c516f-154">Zakończone</span><span class="sxs-lookup"><span data-stu-id="c516f-154">Terminated</span></span>|<span data-ttu-id="c516f-155">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="c516f-155">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="c516f-156">Anulowano</span><span class="sxs-lookup"><span data-stu-id="c516f-156">Unsuspended</span></span>|<span data-ttu-id="c516f-157">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c516f-157">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c516f-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="c516f-158">Example</span></span>  
 <span data-ttu-id="c516f-159">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="c516f-159">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c516f-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c516f-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c516f-161">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c516f-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c516f-162">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c516f-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
