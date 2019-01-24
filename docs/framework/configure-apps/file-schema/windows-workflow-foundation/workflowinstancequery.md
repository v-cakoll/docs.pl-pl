---
title: '&lt;workflowInstanceQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: bef9ddcee2e373f4588d6aed06b7c51e4c6ed4b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662052"
---
# <a name="ltworkflowinstancequerygt"></a><span data-ttu-id="e97e8-102">&lt;workflowInstanceQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e97e8-102">&lt;workflowInstanceQuery&gt;</span></span>
<span data-ttu-id="e97e8-103">Reprezentuje zapytanie, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="e97e8-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="e97e8-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e97e8-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e97e8-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e97e8-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e97e8-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e97e8-106">\<tracking></span></span>  
<span data-ttu-id="e97e8-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e97e8-107">\<trackingProfile></span></span>  
<span data-ttu-id="e97e8-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e97e8-108">\<workflow></span></span>  
<span data-ttu-id="e97e8-109">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="e97e8-109">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="e97e8-110">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="e97e8-110">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97e8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e97e8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e97e8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e97e8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e97e8-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e97e8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e97e8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e97e8-114">Attributes</span></span>  
 <span data-ttu-id="e97e8-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="e97e8-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e97e8-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e97e8-116">Child Elements</span></span>  
  
|<span data-ttu-id="e97e8-117">Element</span><span class="sxs-lookup"><span data-stu-id="e97e8-117">Element</span></span>|<span data-ttu-id="e97e8-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e97e8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97e8-119">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="e97e8-119">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)|<span data-ttu-id="e97e8-120">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="e97e8-120">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e97e8-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e97e8-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e97e8-122">Element</span><span class="sxs-lookup"><span data-stu-id="e97e8-122">Element</span></span>|<span data-ttu-id="e97e8-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e97e8-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97e8-124">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="e97e8-124">\<workflowInstanceQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequeries.md)|<span data-ttu-id="e97e8-125">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="e97e8-125">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e97e8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e97e8-126">Remarks</span></span>  
 <span data-ttu-id="e97e8-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="e97e8-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
-   <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="e97e8-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="e97e8-128">Example</span></span>  
 <span data-ttu-id="e97e8-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e97e8-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e97e8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e97e8-130">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e97e8-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e97e8-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e97e8-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e97e8-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
