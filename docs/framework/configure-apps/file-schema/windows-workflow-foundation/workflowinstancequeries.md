---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: e54f98c980f60d02377e38d53d9d0eb48581eec0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132486"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="9ad79-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9ad79-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="9ad79-102">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="9ad79-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="9ad79-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9ad79-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9ad79-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ad79-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9ad79-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9ad79-105">\<tracking></span></span>  
<span data-ttu-id="9ad79-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9ad79-106">\<trackingProfile></span></span>  
<span data-ttu-id="9ad79-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9ad79-107">\<workflow></span></span>  
<span data-ttu-id="9ad79-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="9ad79-108">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad79-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ad79-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ad79-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ad79-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ad79-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ad79-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ad79-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ad79-112">Attributes</span></span>  
 <span data-ttu-id="9ad79-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ad79-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9ad79-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ad79-114">Child Elements</span></span>  
  
|<span data-ttu-id="9ad79-115">Element</span><span class="sxs-lookup"><span data-stu-id="9ad79-115">Element</span></span>|<span data-ttu-id="9ad79-116">Opis</span><span class="sxs-lookup"><span data-stu-id="9ad79-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad79-117">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="9ad79-117">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="9ad79-118">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9ad79-118">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ad79-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ad79-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9ad79-120">Element</span><span class="sxs-lookup"><span data-stu-id="9ad79-120">Element</span></span>|<span data-ttu-id="9ad79-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9ad79-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ad79-122">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9ad79-122">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9ad79-123">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ad79-123">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ad79-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ad79-124">Remarks</span></span>  
 <span data-ttu-id="9ad79-125"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="9ad79-125">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="9ad79-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ad79-126">Example</span></span>  
 <span data-ttu-id="9ad79-127">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="9ad79-127">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ad79-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ad79-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ad79-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ad79-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ad79-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9ad79-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
