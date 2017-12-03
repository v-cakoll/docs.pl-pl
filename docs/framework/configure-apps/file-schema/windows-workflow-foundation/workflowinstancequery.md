---
title: '&lt;workflowInstanceQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7d9d19c4ea5ecd5dc7a7329eb3fdad657567864
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="45339-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="45339-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="45339-103">Reprezentuje kwerendę, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="45339-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="45339-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="45339-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="45339-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="45339-105">\<system.serviceModel></span></span>  
<span data-ttu-id="45339-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="45339-106">\<tracking></span></span>  
<span data-ttu-id="45339-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="45339-107">\<trackingProfile></span></span>  
<span data-ttu-id="45339-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="45339-108">\<workflow></span></span>  
<span data-ttu-id="45339-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="45339-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="45339-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="45339-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45339-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="45339-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45339-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="45339-112">Attributes and Elements</span></span>  
 <span data-ttu-id="45339-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="45339-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45339-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="45339-114">Attributes</span></span>  
 <span data-ttu-id="45339-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="45339-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="45339-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="45339-116">Child Elements</span></span>  
  
|<span data-ttu-id="45339-117">Element</span><span class="sxs-lookup"><span data-stu-id="45339-117">Element</span></span>|<span data-ttu-id="45339-118">Opis</span><span class="sxs-lookup"><span data-stu-id="45339-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45339-119">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="45339-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="45339-120">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="45339-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45339-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="45339-121">Parent Elements</span></span>  
  
|<span data-ttu-id="45339-122">Element</span><span class="sxs-lookup"><span data-stu-id="45339-122">Element</span></span>|<span data-ttu-id="45339-123">Opis</span><span class="sxs-lookup"><span data-stu-id="45339-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45339-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="45339-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="45339-125">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="45339-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45339-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45339-126">Remarks</span></span>  
 <span data-ttu-id="45339-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="45339-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="45339-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="45339-128">Example</span></span>  
 <span data-ttu-id="45339-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="45339-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45339-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45339-130">See Also</span></span>  
 <span data-ttu-id="45339-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="45339-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="45339-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="45339-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="45339-133">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="45339-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="45339-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="45339-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
