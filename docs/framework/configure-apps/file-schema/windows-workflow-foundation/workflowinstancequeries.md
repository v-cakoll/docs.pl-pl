---
title: '&lt;workflowInstanceQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a4082de6f1c67b7a0bc26662e2491623b2bba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="8ca71-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="8ca71-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="8ca71-103">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="8ca71-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="8ca71-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8ca71-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8ca71-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8ca71-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8ca71-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8ca71-106">\<tracking></span></span>  
<span data-ttu-id="8ca71-107">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8ca71-107">\<trackingProfile></span></span>  
<span data-ttu-id="8ca71-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8ca71-108">\<workflow></span></span>  
<span data-ttu-id="8ca71-109">\<workflowInstanceQueries ></span><span class="sxs-lookup"><span data-stu-id="8ca71-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca71-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca71-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ca71-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8ca71-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8ca71-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8ca71-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ca71-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8ca71-113">Attributes</span></span>  
 <span data-ttu-id="8ca71-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="8ca71-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8ca71-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8ca71-115">Child Elements</span></span>  
  
|<span data-ttu-id="8ca71-116">Element</span><span class="sxs-lookup"><span data-stu-id="8ca71-116">Element</span></span>|<span data-ttu-id="8ca71-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca71-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ca71-118">\<workflowInstanceQuery ></span><span class="sxs-lookup"><span data-stu-id="8ca71-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="8ca71-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8ca71-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8ca71-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8ca71-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8ca71-121">Element</span><span class="sxs-lookup"><span data-stu-id="8ca71-121">Element</span></span>|<span data-ttu-id="8ca71-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca71-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ca71-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8ca71-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8ca71-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8ca71-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ca71-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ca71-125">Remarks</span></span>  
 <span data-ttu-id="8ca71-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="8ca71-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="8ca71-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ca71-127">Example</span></span>  
 <span data-ttu-id="8ca71-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="8ca71-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ca71-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ca71-129">See Also</span></span>  
 <span data-ttu-id="8ca71-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8ca71-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="8ca71-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8ca71-131"><xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8ca71-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="8ca71-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8ca71-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8ca71-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
