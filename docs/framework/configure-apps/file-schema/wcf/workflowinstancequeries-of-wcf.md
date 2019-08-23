---
title: <workflowInstanceQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: feae65a75f9f0b2b1b398f3f9e80ac4c8d971dcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915305"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="755f2-102">\<workflowInstanceQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="755f2-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="755f2-103">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="755f2-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="755f2-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="755f2-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="755f2-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="755f2-105">\<system.serviceModel></span></span>  
<span data-ttu-id="755f2-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="755f2-106">\<tracking></span></span>  
<span data-ttu-id="755f2-107">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="755f2-107">\<profiles></span></span>  
<span data-ttu-id="755f2-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="755f2-108">\<trackingProfile></span></span>  
<span data-ttu-id="755f2-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="755f2-109">\<workflow></span></span>  
<span data-ttu-id="755f2-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="755f2-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755f2-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="755f2-111">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
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
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="755f2-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="755f2-112">Attributes and elements</span></span>

<span data-ttu-id="755f2-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="755f2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="755f2-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="755f2-114">Attributes</span></span>  

<span data-ttu-id="755f2-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="755f2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="755f2-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="755f2-116">Child elements</span></span>  
  
|<span data-ttu-id="755f2-117">Element</span><span class="sxs-lookup"><span data-stu-id="755f2-117">Element</span></span>|<span data-ttu-id="755f2-118">Opis</span><span class="sxs-lookup"><span data-stu-id="755f2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="755f2-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="755f2-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="755f2-120">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="755f2-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="755f2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="755f2-121">Parent elements</span></span>  
  
|<span data-ttu-id="755f2-122">Element</span><span class="sxs-lookup"><span data-stu-id="755f2-122">Element</span></span>|<span data-ttu-id="755f2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="755f2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="755f2-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="755f2-124">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="755f2-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) .</span><span class="sxs-lookup"><span data-stu-id="755f2-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="755f2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="755f2-126">Remarks</span></span>

<span data-ttu-id="755f2-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="755f2-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="755f2-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="755f2-128">Example</span></span>  

<span data-ttu-id="755f2-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="755f2-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="755f2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="755f2-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="755f2-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="755f2-131">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="755f2-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="755f2-132">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
