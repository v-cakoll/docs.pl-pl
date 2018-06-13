---
title: '&lt;workflowInstanceQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 02bb0be83158fddf5907465db5a12a4708461ecb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767465"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="d67b8-102">&lt;workflowInstanceQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="d67b8-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="d67b8-103">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia rozpoczęte lub zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d67b8-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="d67b8-104">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d67b8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="d67b8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d67b8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d67b8-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d67b8-106">\<tracking></span></span>  
<span data-ttu-id="d67b8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d67b8-107">\<trackingProfile></span></span>  
<span data-ttu-id="d67b8-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d67b8-108">\<workflow></span></span>  
<span data-ttu-id="d67b8-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="d67b8-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d67b8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d67b8-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d67b8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d67b8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d67b8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d67b8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d67b8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d67b8-113">Attributes</span></span>  
 <span data-ttu-id="d67b8-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d67b8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d67b8-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d67b8-115">Child Elements</span></span>  
  
|<span data-ttu-id="d67b8-116">Element</span><span class="sxs-lookup"><span data-stu-id="d67b8-116">Element</span></span>|<span data-ttu-id="d67b8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d67b8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d67b8-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="d67b8-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="d67b8-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d67b8-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d67b8-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d67b8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d67b8-121">Element</span><span class="sxs-lookup"><span data-stu-id="d67b8-121">Element</span></span>|<span data-ttu-id="d67b8-122">Opis</span><span class="sxs-lookup"><span data-stu-id="d67b8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d67b8-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d67b8-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="d67b8-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez [obiektu activityDefinitionId](http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="d67b8-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d67b8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d67b8-125">Remarks</span></span>  
 <span data-ttu-id="d67b8-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="d67b8-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="d67b8-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d67b8-127">Example</span></span>  
 <span data-ttu-id="d67b8-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="d67b8-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d67b8-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d67b8-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="d67b8-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d67b8-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d67b8-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d67b8-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
