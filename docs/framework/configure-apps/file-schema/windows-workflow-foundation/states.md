---
title: <states>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ebea5e7c-ad58-43c5-8f2d-cca25ae1b721
ms.openlocfilehash: 1a7c839a5ff8fac9470aea71a4886d9000086e9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398618"
---
# \<states>
<span data-ttu-id="2e6d1-101">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-101">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
 <span data-ttu-id="2e6d1-102">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2e6d1-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="2e6d1-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e6d1-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e6d1-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2e6d1-104">Attributes and Elements</span></span>  
 <span data-ttu-id="2e6d1-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e6d1-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2e6d1-106">Attributes</span></span>  
 <span data-ttu-id="2e6d1-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e6d1-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2e6d1-108">Child Elements</span></span>  
  
|<span data-ttu-id="2e6d1-109">Element</span><span class="sxs-lookup"><span data-stu-id="2e6d1-109">Element</span></span>|<span data-ttu-id="2e6d1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="2e6d1-110">Description</span></span>|  
|-------------|-----------------|  
|[\<state>](states.md)|<span data-ttu-id="2e6d1-111">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-111">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e6d1-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2e6d1-112">Parent Elements</span></span>  
  
|<span data-ttu-id="2e6d1-113">Element</span><span class="sxs-lookup"><span data-stu-id="2e6d1-113">Element</span></span>|<span data-ttu-id="2e6d1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2e6d1-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](workflowinstancequery.md)|<span data-ttu-id="2e6d1-115">Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-115">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e6d1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e6d1-116">Remarks</span></span>  
 <span data-ttu-id="2e6d1-117">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-117">The returned records are filtered by the states in this collection.</span></span>  
  
 <span data-ttu-id="2e6d1-118">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-118">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="2e6d1-119">Stan</span><span class="sxs-lookup"><span data-stu-id="2e6d1-119">State</span></span>|<span data-ttu-id="2e6d1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2e6d1-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2e6d1-121">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="2e6d1-121">Aborted</span></span>|<span data-ttu-id="2e6d1-122">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-122">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="2e6d1-123">Ukończone</span><span class="sxs-lookup"><span data-stu-id="2e6d1-123">Completed</span></span>|<span data-ttu-id="2e6d1-124">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-124">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="2e6d1-125">Usunięte</span><span class="sxs-lookup"><span data-stu-id="2e6d1-125">Deleted</span></span>|<span data-ttu-id="2e6d1-126">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-126">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="2e6d1-127">Okresy</span><span class="sxs-lookup"><span data-stu-id="2e6d1-127">Idle</span></span>|<span data-ttu-id="2e6d1-128">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-128">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="2e6d1-129">Trwały</span><span class="sxs-lookup"><span data-stu-id="2e6d1-129">Persisted</span></span>|<span data-ttu-id="2e6d1-130">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-130">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="2e6d1-131">Wznowione</span><span class="sxs-lookup"><span data-stu-id="2e6d1-131">Resumed</span></span>|<span data-ttu-id="2e6d1-132">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-132">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="2e6d1-133">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="2e6d1-133">Started</span></span>|<span data-ttu-id="2e6d1-134">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-134">The workflow instance is started.</span></span>|  
|<span data-ttu-id="2e6d1-135">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="2e6d1-135">UnhandledException</span></span>|<span data-ttu-id="2e6d1-136">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-136">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="2e6d1-137">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="2e6d1-137">Unloaded</span></span>|<span data-ttu-id="2e6d1-138">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-138">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="2e6d1-139">Anulowane</span><span class="sxs-lookup"><span data-stu-id="2e6d1-139">Canceled</span></span>|<span data-ttu-id="2e6d1-140">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-140">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="2e6d1-141">Suspended</span><span class="sxs-lookup"><span data-stu-id="2e6d1-141">Suspended</span></span>|<span data-ttu-id="2e6d1-142">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-142">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="2e6d1-143">Zakończone</span><span class="sxs-lookup"><span data-stu-id="2e6d1-143">Terminated</span></span>|<span data-ttu-id="2e6d1-144">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-144">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="2e6d1-145">Anulowano</span><span class="sxs-lookup"><span data-stu-id="2e6d1-145">Unsuspended</span></span>|<span data-ttu-id="2e6d1-146">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-146">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2e6d1-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e6d1-147">Example</span></span>  
 <span data-ttu-id="2e6d1-148">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="2e6d1-148">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e6d1-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e6d1-149">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="2e6d1-150">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2e6d1-150">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2e6d1-151">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2e6d1-151">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
