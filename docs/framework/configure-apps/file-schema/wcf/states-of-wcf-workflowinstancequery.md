---
title: <states>programu WCF,<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: 5b779cf1074687dbd648b23d04f7cf3a354a2014
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855027"
---
# <a name="states-of-wcf-workflowinstancequery"></a><span data-ttu-id="1e3d4-102">\<states>programu WCF,\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="1e3d4-102">\<states> of WCF, \<workflowInstanceQuery></span></span>

<span data-ttu-id="1e3d4-103">Reprezentuje kolekcję subskrybowanego stanów z wystąpienia śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-103">Represents a collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>  
  
<span data-ttu-id="1e3d4-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="1e3d4-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQuery>**](workflowinstancequery-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<states>**  
  
## <a name="syntax"></a><span data-ttu-id="1e3d4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e3d4-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e3d4-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1e3d4-106">Attributes and elements</span></span>

<span data-ttu-id="1e3d4-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e3d4-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1e3d4-108">Attributes</span></span>  

<span data-ttu-id="1e3d4-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e3d4-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1e3d4-110">Child elements</span></span>
  
|<span data-ttu-id="1e3d4-111">Element</span><span class="sxs-lookup"><span data-stu-id="1e3d4-111">Element</span></span>|<span data-ttu-id="1e3d4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1e3d4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|<span data-ttu-id="1e3d4-113">Stan subskrybowanego z wystąpienia elementu śledzonych przepływu pracy podczas rekordem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-113">A subscribed state from the tracked workflow instance when the tracking record is created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e3d4-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1e3d4-114">Parent elements</span></span>  
  
|<span data-ttu-id="1e3d4-115">Element</span><span class="sxs-lookup"><span data-stu-id="1e3d4-115">Element</span></span>|<span data-ttu-id="1e3d4-116">Opis</span><span class="sxs-lookup"><span data-stu-id="1e3d4-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="1e3d4-117">Zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-117">A query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e3d4-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e3d4-118">Remarks</span></span>

<span data-ttu-id="1e3d4-119">Zwracane rekordy są filtrowane według stanów w tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-119">The returned records are filtered by the states in this collection.</span></span>  
  
<span data-ttu-id="1e3d4-120">Stan możliwe wartości są opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-120">Possible state values are described in the following table.</span></span>  
  
|<span data-ttu-id="1e3d4-121">Stan</span><span class="sxs-lookup"><span data-stu-id="1e3d4-121">State</span></span>|<span data-ttu-id="1e3d4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="1e3d4-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e3d4-123">Zostało przerwane</span><span class="sxs-lookup"><span data-stu-id="1e3d4-123">Aborted</span></span>|<span data-ttu-id="1e3d4-124">Wystąpienie przepływu pracy zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-124">The workflow instance is aborted.</span></span>|  
|<span data-ttu-id="1e3d4-125">Ukończone</span><span class="sxs-lookup"><span data-stu-id="1e3d4-125">Completed</span></span>|<span data-ttu-id="1e3d4-126">Wystąpienie przepływu pracy zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-126">The workflow instance is completed.</span></span>|  
|<span data-ttu-id="1e3d4-127">Usunięte</span><span class="sxs-lookup"><span data-stu-id="1e3d4-127">Deleted</span></span>|<span data-ttu-id="1e3d4-128">Wystąpienie przepływu pracy, został usunięty.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-128">The workflow instance is deleted.</span></span>|  
|<span data-ttu-id="1e3d4-129">Okresy</span><span class="sxs-lookup"><span data-stu-id="1e3d4-129">Idle</span></span>|<span data-ttu-id="1e3d4-130">Wystąpienie przepływu pracy jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-130">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="1e3d4-131">Trwały</span><span class="sxs-lookup"><span data-stu-id="1e3d4-131">Persisted</span></span>|<span data-ttu-id="1e3d4-132">Wystąpienie przepływu pracy jest trwały.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-132">The workflow instance is persisted.</span></span>|  
|<span data-ttu-id="1e3d4-133">Wznowione</span><span class="sxs-lookup"><span data-stu-id="1e3d4-133">Resumed</span></span>|<span data-ttu-id="1e3d4-134">Wystąpienie przepływu pracy zostanie wznowione.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-134">The workflow instance is resumed.</span></span>|  
|<span data-ttu-id="1e3d4-135">Rozpoczęto</span><span class="sxs-lookup"><span data-stu-id="1e3d4-135">Started</span></span>|<span data-ttu-id="1e3d4-136">Wystąpienie przepływu pracy zostało rozpoczęte.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-136">The workflow instance is started.</span></span>|  
|<span data-ttu-id="1e3d4-137">UnhandledException</span><span class="sxs-lookup"><span data-stu-id="1e3d4-137">UnhandledException</span></span>|<span data-ttu-id="1e3d4-138">Wystąpienie przepływu pracy napotkał nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-138">The workflow instance encountered an unhandled exception.</span></span>|  
|<span data-ttu-id="1e3d4-139">Zwolniono</span><span class="sxs-lookup"><span data-stu-id="1e3d4-139">Unloaded</span></span>|<span data-ttu-id="1e3d4-140">Wystąpienie przepływu pracy nie jest załadowany.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-140">The workflow instance is unloaded.</span></span>|  
|<span data-ttu-id="1e3d4-141">Anulowane</span><span class="sxs-lookup"><span data-stu-id="1e3d4-141">Canceled</span></span>|<span data-ttu-id="1e3d4-142">Wystąpienie przepływu pracy zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-142">The workflow instance is canceled.</span></span>|  
|<span data-ttu-id="1e3d4-143">Suspended</span><span class="sxs-lookup"><span data-stu-id="1e3d4-143">Suspended</span></span>|<span data-ttu-id="1e3d4-144">Wystąpienie przepływu pracy jest zawieszone.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-144">The workflow instance is suspended.</span></span>|  
|<span data-ttu-id="1e3d4-145">Zakończone</span><span class="sxs-lookup"><span data-stu-id="1e3d4-145">Terminated</span></span>|<span data-ttu-id="1e3d4-146">Wystąpienie przepływu pracy jest zakończone.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-146">The workflow instance is terminated.</span></span>|  
|<span data-ttu-id="1e3d4-147">Anulowano</span><span class="sxs-lookup"><span data-stu-id="1e3d4-147">Unsuspended</span></span>|<span data-ttu-id="1e3d4-148">Anulowano to wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-148">The workflow instance is unsuspended.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e3d4-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e3d4-149">Example</span></span>

<span data-ttu-id="1e3d4-150">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="1e3d4-150">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="1e3d4-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e3d4-151">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="1e3d4-152">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1e3d4-152">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="1e3d4-153">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="1e3d4-153">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
