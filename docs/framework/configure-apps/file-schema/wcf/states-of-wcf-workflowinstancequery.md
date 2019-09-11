---
title: <states>programu WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855027"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="717f4-102">\<Stany > WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="717f4-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="717f4-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="717f4-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="717f4-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="717f4-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="717f4-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="717f4-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="717f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="717f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="717f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="717f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="717f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="717f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="717f4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="717f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Stany >**</span><span class="sxs-lookup"><span data-stu-id="717f4-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="717f4-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="717f4-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="717f4-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="717f4-115">Attributes and elements</span></span>

<span data-ttu-id="717f4-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="717f4-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="717f4-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="717f4-117">Attributes</span></span>  

<span data-ttu-id="717f4-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="717f4-118">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="717f4-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="717f4-119">Child elements</span></span>
  
|<span data-ttu-id="717f4-120">Element</span><span class="sxs-lookup"><span data-stu-id="717f4-120">Element</span></span>|<span data-ttu-id="717f4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="717f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="717f4-122">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="717f4-122">\<states></span></span>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="717f4-123">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="717f4-123">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="717f4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="717f4-124">Parent elements</span></span>  
  
|<span data-ttu-id="717f4-125">Element</span><span class="sxs-lookup"><span data-stu-id="717f4-125">Element</span></span>|<span data-ttu-id="717f4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="717f4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="717f4-127">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="717f4-127">\<workflowInstanceQuery></span></span>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="717f4-128">Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="717f4-128">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="717f4-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="717f4-129">Remarks</span></span>

<span data-ttu-id="717f4-130">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="717f4-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="717f4-131">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="717f4-131">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="717f4-132">Stan</span><span class="sxs-lookup"><span data-stu-id="717f4-132">State</span></span>|<span data-ttu-id="717f4-133">Opis</span><span class="sxs-lookup"><span data-stu-id="717f4-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="717f4-134">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="717f4-134">Aborted</span></span>|<span data-ttu-id="717f4-135">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="717f4-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="717f4-136">Zakończone</span><span class="sxs-lookup"><span data-stu-id="717f4-136">Completed</span></span>|<span data-ttu-id="717f4-137">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="717f4-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="717f4-138">Usunięte</span><span class="sxs-lookup"><span data-stu-id="717f4-138">Deleted</span></span>|<span data-ttu-id="717f4-139">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="717f4-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="717f4-140">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="717f4-140">Idle</span></span>|<span data-ttu-id="717f4-141">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="717f4-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="717f4-142">Trwały</span><span class="sxs-lookup"><span data-stu-id="717f4-142">Persisted</span></span>|<span data-ttu-id="717f4-143">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="717f4-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="717f4-144">Wznowione</span><span class="sxs-lookup"><span data-stu-id="717f4-144">Resumed</span></span>|<span data-ttu-id="717f4-145">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="717f4-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="717f4-146">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="717f4-146">Started</span></span>|<span data-ttu-id="717f4-147">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="717f4-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="717f4-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="717f4-148">UnhandledException</span></span>|<span data-ttu-id="717f4-149">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="717f4-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="717f4-150">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="717f4-150">Unloaded</span></span>|<span data-ttu-id="717f4-151">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="717f4-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="717f4-152">Anulowane</span><span class="sxs-lookup"><span data-stu-id="717f4-152">Canceled</span></span>|<span data-ttu-id="717f4-153">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="717f4-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="717f4-154">Suspended</span><span class="sxs-lookup"><span data-stu-id="717f4-154">Suspended</span></span>|<span data-ttu-id="717f4-155">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="717f4-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="717f4-156">Zakończone</span><span class="sxs-lookup"><span data-stu-id="717f4-156">Terminated</span></span>|<span data-ttu-id="717f4-157">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="717f4-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="717f4-158">Anulowano</span><span class="sxs-lookup"><span data-stu-id="717f4-158">Unsuspended</span></span>|<span data-ttu-id="717f4-159">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="717f4-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="717f4-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="717f4-160">Example</span></span>

<span data-ttu-id="717f4-161">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="717f4-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="717f4-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="717f4-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="717f4-163">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="717f4-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="717f4-164">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="717f4-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
