---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 88ad61dca6c0f756a14538e7b207532ff7173ec5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624747"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="67170-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="67170-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="67170-102">Reprezentuje zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="67170-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="67170-103">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="67170-103">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="67170-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="67170-104">\<system.serviceModel></span></span>  
<span data-ttu-id="67170-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="67170-105">\<tracking></span></span>  
<span data-ttu-id="67170-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="67170-106">\<trackingProfile></span></span>  
<span data-ttu-id="67170-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="67170-107">\<workflow></span></span>  
<span data-ttu-id="67170-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="67170-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="67170-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="67170-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67170-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="67170-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67170-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67170-111">Attributes and Elements</span></span>  
 <span data-ttu-id="67170-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67170-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67170-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67170-113">Attributes</span></span>  
 <span data-ttu-id="67170-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="67170-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67170-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67170-115">Child Elements</span></span>  
  
|<span data-ttu-id="67170-116">Element</span><span class="sxs-lookup"><span data-stu-id="67170-116">Element</span></span>|<span data-ttu-id="67170-117">Opis</span><span class="sxs-lookup"><span data-stu-id="67170-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67170-118">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="67170-118">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="67170-119">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="67170-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67170-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67170-120">Parent Elements</span></span>  
  
|<span data-ttu-id="67170-121">Element</span><span class="sxs-lookup"><span data-stu-id="67170-121">Element</span></span>|<span data-ttu-id="67170-122">Opis</span><span class="sxs-lookup"><span data-stu-id="67170-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67170-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="67170-123">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="67170-124">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="67170-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67170-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67170-125">Remarks</span></span>  
 <span data-ttu-id="67170-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="67170-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="67170-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="67170-127">Example</span></span>  
 <span data-ttu-id="67170-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="67170-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67170-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67170-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="67170-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="67170-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="67170-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="67170-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
