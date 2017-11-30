---
title: '&lt;workflowInstanceQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 413e341c31b5312d2d772a901965c3917d05e44f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequerygt-of-wcf"></a><span data-ttu-id="d14fa-102">&lt;workflowInstanceQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="d14fa-102">&lt;workflowInstanceQuery&gt; of WCF</span></span>
<span data-ttu-id="d14fa-103">Reprezentuje kwerendę, która śledzi zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d14fa-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="d14fa-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d14fa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d14fa-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d14fa-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d14fa-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d14fa-106">\<tracking></span></span>  
<span data-ttu-id="d14fa-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d14fa-107">\<trackingProfile></span></span>  
<span data-ttu-id="d14fa-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d14fa-108">\<workflow></span></span>  
<span data-ttu-id="d14fa-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="d14fa-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="d14fa-110">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="d14fa-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d14fa-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="d14fa-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d14fa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d14fa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d14fa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d14fa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d14fa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d14fa-114">Attributes</span></span>  
 <span data-ttu-id="d14fa-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d14fa-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d14fa-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d14fa-116">Child Elements</span></span>  
  
|<span data-ttu-id="d14fa-117">Element</span><span class="sxs-lookup"><span data-stu-id="d14fa-117">Element</span></span>|<span data-ttu-id="d14fa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d14fa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d14fa-119">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="d14fa-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="d14fa-120">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d14fa-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d14fa-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d14fa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d14fa-122">Element</span><span class="sxs-lookup"><span data-stu-id="d14fa-122">Element</span></span>|<span data-ttu-id="d14fa-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d14fa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d14fa-124">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="d14fa-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="d14fa-125">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d14fa-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d14fa-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d14fa-126">Remarks</span></span>  
 <span data-ttu-id="d14fa-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="d14fa-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="d14fa-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="d14fa-128">Example</span></span>  
 <span data-ttu-id="d14fa-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="d14fa-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d14fa-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d14fa-130">See Also</span></span>  
 <span data-ttu-id="d14fa-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d14fa-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d14fa-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d14fa-132"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="d14fa-133">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="d14fa-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d14fa-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d14fa-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
