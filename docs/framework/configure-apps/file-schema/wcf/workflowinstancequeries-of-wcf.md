---
title: '&lt;workflowInstanceQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: dfa75a7e4729244ba5887e6666c0fdfe840e9faf
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425852"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="eb859-102">&lt;workflowInstanceQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="eb859-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>
<span data-ttu-id="eb859-103">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="eb859-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="eb859-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="eb859-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="eb859-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb859-105">\<system.serviceModel></span></span>  
<span data-ttu-id="eb859-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="eb859-106">\<tracking></span></span>  
<span data-ttu-id="eb859-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eb859-107">\<trackingProfile></span></span>  
<span data-ttu-id="eb859-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="eb859-108">\<workflow></span></span>  
<span data-ttu-id="eb859-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="eb859-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb859-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb859-110">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <workflowInstanceQueries>             <workflowInstanceQuery>                <states>                   <state name="Name"/>                </states>            </workflowInstanceQuery>         </workflowInstanceQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb859-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb859-111">Attributes and Elements</span></span>  
 <span data-ttu-id="eb859-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb859-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb859-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb859-113">Attributes</span></span>  
 <span data-ttu-id="eb859-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb859-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb859-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb859-115">Child Elements</span></span>  
  
|<span data-ttu-id="eb859-116">Element</span><span class="sxs-lookup"><span data-stu-id="eb859-116">Element</span></span>|<span data-ttu-id="eb859-117">Opis</span><span class="sxs-lookup"><span data-stu-id="eb859-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb859-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="eb859-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="eb859-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="eb859-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb859-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb859-120">Parent Elements</span></span>  
  
|<span data-ttu-id="eb859-121">Element</span><span class="sxs-lookup"><span data-stu-id="eb859-121">Element</span></span>|<span data-ttu-id="eb859-122">Opis</span><span class="sxs-lookup"><span data-stu-id="eb859-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb859-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="eb859-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="eb859-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb859-124">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb859-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb859-125">Remarks</span></span>  
 <span data-ttu-id="eb859-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="eb859-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="eb859-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb859-127">Example</span></span>  
 <span data-ttu-id="eb859-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="eb859-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb859-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb859-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="eb859-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="eb859-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eb859-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="eb859-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
