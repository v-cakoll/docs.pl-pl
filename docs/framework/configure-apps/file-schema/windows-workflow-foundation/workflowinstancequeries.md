---
title: '&lt;workflowInstanceQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 8ee8c74e88f1605ae3858db787c38976de9cc976
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693707"
---
# <a name="ltworkflowinstancequeriesgt"></a><span data-ttu-id="fa400-102">&lt;workflowInstanceQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="fa400-102">&lt;workflowInstanceQueries&gt;</span></span>
<span data-ttu-id="fa400-103">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="fa400-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="fa400-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fa400-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fa400-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fa400-105">\<system.serviceModel></span></span>  
<span data-ttu-id="fa400-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="fa400-106">\<tracking></span></span>  
<span data-ttu-id="fa400-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="fa400-107">\<trackingProfile></span></span>  
<span data-ttu-id="fa400-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="fa400-108">\<workflow></span></span>  
<span data-ttu-id="fa400-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="fa400-109">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa400-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="fa400-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa400-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fa400-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fa400-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fa400-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa400-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fa400-113">Attributes</span></span>  
 <span data-ttu-id="fa400-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="fa400-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fa400-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fa400-115">Child Elements</span></span>  
  
|<span data-ttu-id="fa400-116">Element</span><span class="sxs-lookup"><span data-stu-id="fa400-116">Element</span></span>|<span data-ttu-id="fa400-117">Opis</span><span class="sxs-lookup"><span data-stu-id="fa400-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa400-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="fa400-118">\<workflowInstanceQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|<span data-ttu-id="fa400-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="fa400-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fa400-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fa400-120">Parent Elements</span></span>  
  
|<span data-ttu-id="fa400-121">Element</span><span class="sxs-lookup"><span data-stu-id="fa400-121">Element</span></span>|<span data-ttu-id="fa400-122">Opis</span><span class="sxs-lookup"><span data-stu-id="fa400-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa400-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="fa400-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="fa400-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="fa400-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa400-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fa400-125">Remarks</span></span>  
 <span data-ttu-id="fa400-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="fa400-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="fa400-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="fa400-127">Example</span></span>  
 <span data-ttu-id="fa400-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="fa400-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa400-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fa400-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fa400-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fa400-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fa400-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="fa400-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
