---
title: <state>programu WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 80f7532f3c51680a2e34713b526dc43822db61b9
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854949"
---
# <a name="state-of-wcf-workflowinstancequery"></a><span data-ttu-id="8bf8e-102">\<> stanu WCF, \<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="8bf8e-102">\<state> of WCF, \<workflowInstanceQuery></span></span>
<span data-ttu-id="8bf8e-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="8bf8e-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8bf8e-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8bf8e-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8bf8e-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="8bf8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="8bf8e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="8bf8e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="8bf8e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="8bf8e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="8bf8e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQuery >** ](workflowinstancequery-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)</span></span>\
<span data-ttu-id="8bf8e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Stany >** ](states-of-wcf-workflowinstancequery.md)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<states>**](states-of-wcf-workflowinstancequery.md)</span></span>\
<span data-ttu-id="8bf8e-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> stanu**</span><span class="sxs-lookup"><span data-stu-id="8bf8e-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<state>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bf8e-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bf8e-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8bf8e-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8bf8e-116">Attributes and elements</span></span>

<span data-ttu-id="8bf8e-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="8bf8e-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8bf8e-118">Attributes</span></span>

|<span data-ttu-id="8bf8e-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8bf8e-119">Attribute</span></span>|<span data-ttu-id="8bf8e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf8e-120">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="8bf8e-121">Ciąg, który określa subskrybowanego stanu z wystąpienia śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-121">A string that specifies a subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8bf8e-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8bf8e-122">Child elements</span></span>

<span data-ttu-id="8bf8e-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8bf8e-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8bf8e-124">Parent elements</span></span>

|<span data-ttu-id="8bf8e-125">Element</span><span class="sxs-lookup"><span data-stu-id="8bf8e-125">Element</span></span>|<span data-ttu-id="8bf8e-126">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf8e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8bf8e-127">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="8bf8e-127">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="8bf8e-128">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-128">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf8e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8bf8e-129">Remarks</span></span>  

<span data-ttu-id="8bf8e-130">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-130">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="8bf8e-131">Możliwe wartości stanu są opisane w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="8bf8e-131">Possible state values are described in the following table:</span></span>
  
|<span data-ttu-id="8bf8e-132">Stan</span><span class="sxs-lookup"><span data-stu-id="8bf8e-132">State</span></span>|<span data-ttu-id="8bf8e-133">Opis</span><span class="sxs-lookup"><span data-stu-id="8bf8e-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8bf8e-134">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="8bf8e-134">Aborted</span></span>|<span data-ttu-id="8bf8e-135">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-135">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="8bf8e-136">Zakończone</span><span class="sxs-lookup"><span data-stu-id="8bf8e-136">Completed</span></span>|<span data-ttu-id="8bf8e-137">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-137">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="8bf8e-138">Usunięte</span><span class="sxs-lookup"><span data-stu-id="8bf8e-138">Deleted</span></span>|<span data-ttu-id="8bf8e-139">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-139">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="8bf8e-140">Bezczynności (%)</span><span class="sxs-lookup"><span data-stu-id="8bf8e-140">Idle</span></span>|<span data-ttu-id="8bf8e-141">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-141">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="8bf8e-142">Trwały</span><span class="sxs-lookup"><span data-stu-id="8bf8e-142">Persisted</span></span>|<span data-ttu-id="8bf8e-143">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-143">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="8bf8e-144">Wznowione</span><span class="sxs-lookup"><span data-stu-id="8bf8e-144">Resumed</span></span>|<span data-ttu-id="8bf8e-145">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-145">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="8bf8e-146">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="8bf8e-146">Started</span></span>|<span data-ttu-id="8bf8e-147">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-147">The workflow instance is started.</span></span>|  
|<span data-ttu-id="8bf8e-148">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="8bf8e-148">UnhandledException</span></span>|<span data-ttu-id="8bf8e-149">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-149">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="8bf8e-150">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="8bf8e-150">Unloaded</span></span>|<span data-ttu-id="8bf8e-151">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-151">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="8bf8e-152">Anulowane</span><span class="sxs-lookup"><span data-stu-id="8bf8e-152">Canceled</span></span>|<span data-ttu-id="8bf8e-153">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-153">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="8bf8e-154">Suspended</span><span class="sxs-lookup"><span data-stu-id="8bf8e-154">Suspended</span></span>|<span data-ttu-id="8bf8e-155">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-155">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="8bf8e-156">Zakończone</span><span class="sxs-lookup"><span data-stu-id="8bf8e-156">Terminated</span></span>|<span data-ttu-id="8bf8e-157">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-157">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="8bf8e-158">Anulowano</span><span class="sxs-lookup"><span data-stu-id="8bf8e-158">Unsuspended</span></span>|<span data-ttu-id="8bf8e-159">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-159">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8bf8e-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bf8e-160">Example</span></span>

<span data-ttu-id="8bf8e-161">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="8bf8e-161">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="8bf8e-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bf8e-162">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8bf8e-163">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8bf8e-163">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8bf8e-164">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8bf8e-164">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
