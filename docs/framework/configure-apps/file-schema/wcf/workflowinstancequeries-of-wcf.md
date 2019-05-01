---
title: <workflowInstanceQueries> w WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 89e122b87743a81a80ce63b382ae235c1c4863bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790523"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="13d1b-102">\<workflowInstanceQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="13d1b-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="13d1b-103">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="13d1b-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="13d1b-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="13d1b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="13d1b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="13d1b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="13d1b-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="13d1b-106">\<tracking></span></span>  
<span data-ttu-id="13d1b-107">\<profiles></span><span class="sxs-lookup"><span data-stu-id="13d1b-107">\<profiles></span></span>  
<span data-ttu-id="13d1b-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="13d1b-108">\<trackingProfile></span></span>  
<span data-ttu-id="13d1b-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="13d1b-109">\<workflow></span></span>  
<span data-ttu-id="13d1b-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="13d1b-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13d1b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="13d1b-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13d1b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="13d1b-112">Attributes and elements</span></span>

<span data-ttu-id="13d1b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="13d1b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13d1b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="13d1b-114">Attributes</span></span>  

<span data-ttu-id="13d1b-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="13d1b-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13d1b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="13d1b-116">Child elements</span></span>  
  
|<span data-ttu-id="13d1b-117">Element</span><span class="sxs-lookup"><span data-stu-id="13d1b-117">Element</span></span>|<span data-ttu-id="13d1b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="13d1b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13d1b-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="13d1b-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="13d1b-120">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="13d1b-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13d1b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="13d1b-121">Parent elements</span></span>  
  
|<span data-ttu-id="13d1b-122">Element</span><span class="sxs-lookup"><span data-stu-id="13d1b-122">Element</span></span>|<span data-ttu-id="13d1b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="13d1b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13d1b-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="13d1b-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="13d1b-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) właściwości.</span><span class="sxs-lookup"><span data-stu-id="13d1b-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13d1b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13d1b-126">Remarks</span></span>

<span data-ttu-id="13d1b-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="13d1b-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="13d1b-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="13d1b-128">Example</span></span>  

<span data-ttu-id="13d1b-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="13d1b-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="13d1b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13d1b-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="13d1b-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="13d1b-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="13d1b-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="13d1b-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
