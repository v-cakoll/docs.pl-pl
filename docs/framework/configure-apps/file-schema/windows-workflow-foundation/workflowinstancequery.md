---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: f0a3c3a27b40000432b40b7008f81251fe771ca2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913142"
---
# <a name="workflowinstancequery"></a><span data-ttu-id="4aa1f-101">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4aa1f-101">\<workflowInstanceQuery></span></span>
<span data-ttu-id="4aa1f-102">Reprezentuje zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-102">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="4aa1f-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4aa1f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4aa1f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4aa1f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4aa1f-105">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="4aa1f-105">\<tracking></span></span>  
<span data-ttu-id="4aa1f-106">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4aa1f-106">\<trackingProfile></span></span>  
<span data-ttu-id="4aa1f-107">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4aa1f-107">\<workflow></span></span>  
<span data-ttu-id="4aa1f-108">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="4aa1f-108">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="4aa1f-109">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4aa1f-109">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa1f-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4aa1f-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4aa1f-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4aa1f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4aa1f-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4aa1f-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4aa1f-113">Attributes</span></span>  
 <span data-ttu-id="4aa1f-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4aa1f-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4aa1f-115">Child Elements</span></span>  
  
|<span data-ttu-id="4aa1f-116">Element</span><span class="sxs-lookup"><span data-stu-id="4aa1f-116">Element</span></span>|<span data-ttu-id="4aa1f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4aa1f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aa1f-118">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="4aa1f-118">\<states></span></span>](states.md)|<span data-ttu-id="4aa1f-119">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-119">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4aa1f-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4aa1f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4aa1f-121">Element</span><span class="sxs-lookup"><span data-stu-id="4aa1f-121">Element</span></span>|<span data-ttu-id="4aa1f-122">Opis</span><span class="sxs-lookup"><span data-stu-id="4aa1f-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4aa1f-123">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="4aa1f-123">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="4aa1f-124">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-124">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aa1f-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4aa1f-125">Remarks</span></span>  
 <span data-ttu-id="4aa1f-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="4aa1f-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4aa1f-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="4aa1f-127">Example</span></span>  
 <span data-ttu-id="4aa1f-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="4aa1f-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aa1f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4aa1f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4aa1f-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4aa1f-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4aa1f-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4aa1f-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
