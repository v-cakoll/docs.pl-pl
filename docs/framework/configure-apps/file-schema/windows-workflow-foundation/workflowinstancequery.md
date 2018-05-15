---
title: '&lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: eb8b84f70025df3a8a8ac96f61dec6755eb3a364
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="9d57d-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="9d57d-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="9d57d-103">Reprezentuje kwerendę, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="9d57d-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="9d57d-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9d57d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9d57d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d57d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9d57d-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9d57d-106">\<tracking></span></span>  
<span data-ttu-id="9d57d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9d57d-107">\<trackingProfile></span></span>  
<span data-ttu-id="9d57d-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9d57d-108">\<workflow></span></span>  
<span data-ttu-id="9d57d-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9d57d-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="9d57d-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="9d57d-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d57d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d57d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d57d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d57d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9d57d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d57d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d57d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d57d-114">Attributes</span></span>  
 <span data-ttu-id="9d57d-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d57d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d57d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d57d-116">Child Elements</span></span>  
  
|<span data-ttu-id="9d57d-117">Element</span><span class="sxs-lookup"><span data-stu-id="9d57d-117">Element</span></span>|<span data-ttu-id="9d57d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9d57d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d57d-119">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="9d57d-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="9d57d-120">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9d57d-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d57d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d57d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d57d-122">Element</span><span class="sxs-lookup"><span data-stu-id="9d57d-122">Element</span></span>|<span data-ttu-id="9d57d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9d57d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d57d-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9d57d-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="9d57d-125">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="9d57d-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d57d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d57d-126">Remarks</span></span>  
 <span data-ttu-id="9d57d-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="9d57d-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9d57d-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d57d-128">Example</span></span>  
 <span data-ttu-id="9d57d-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="9d57d-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d57d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d57d-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="9d57d-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9d57d-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="9d57d-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9d57d-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
