---
title: '&lt;workflowInstanceQueries&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6ca8104ba2470593e07e03a7fe0bc80c9cd2f6a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="e1460-102">&lt;workflowInstanceQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="e1460-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="e1460-103">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="e1460-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="e1460-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e1460-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e1460-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e1460-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e1460-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e1460-106">\<tracking></span></span>  
<span data-ttu-id="e1460-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e1460-107">\<trackingProfile></span></span>  
<span data-ttu-id="e1460-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e1460-108">\<workflow></span></span>  
<span data-ttu-id="e1460-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="e1460-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1460-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1460-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1460-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1460-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e1460-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1460-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1460-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1460-113">Attributes</span></span>  
 <span data-ttu-id="e1460-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1460-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1460-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1460-115">Child Elements</span></span>  
  
|<span data-ttu-id="e1460-116">Element</span><span class="sxs-lookup"><span data-stu-id="e1460-116">Element</span></span>|<span data-ttu-id="e1460-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e1460-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1460-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="e1460-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="e1460-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e1460-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1460-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1460-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e1460-121">Element</span><span class="sxs-lookup"><span data-stu-id="e1460-121">Element</span></span>|<span data-ttu-id="e1460-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e1460-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1460-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e1460-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e1460-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez [obiektu activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="e1460-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1460-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1460-125">Remarks</span></span>  
 <span data-ttu-id="e1460-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="e1460-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e1460-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1460-127">Example</span></span>  
 <span data-ttu-id="e1460-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e1460-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1460-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1460-129">See Also</span></span>  
 <span data-ttu-id="e1460-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1460-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="e1460-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e1460-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="e1460-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="e1460-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e1460-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e1460-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
