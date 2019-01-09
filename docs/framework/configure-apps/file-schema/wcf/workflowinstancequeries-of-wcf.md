---
title: '&lt;workflowInstanceQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: e3ad1139781c54cc1ca4e2d2b264f3f375b49108
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145565"
---
# <a name="ltworkflowinstancequeriesgt-of-wcf"></a><span data-ttu-id="c6c31-102">&lt;workflowInstanceQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="c6c31-102">&lt;workflowInstanceQueries&gt; of WCF</span></span>

<span data-ttu-id="c6c31-103">Reprezentuje kolekcję elementów konfiguracji, które śledzenie zmian cyklu życia wystąpienia przepływu pracy, takich jak zdarzenia uruchomiona lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="c6c31-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="c6c31-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c6c31-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="c6c31-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c6c31-105">\<system.serviceModel></span></span>  
<span data-ttu-id="c6c31-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="c6c31-106">\<tracking></span></span>  
<span data-ttu-id="c6c31-107">\<profile ></span><span class="sxs-lookup"><span data-stu-id="c6c31-107">\<profiles></span></span>  
<span data-ttu-id="c6c31-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c6c31-108">\<trackingProfile></span></span>  
<span data-ttu-id="c6c31-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="c6c31-109">\<workflow></span></span>  
<span data-ttu-id="c6c31-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="c6c31-110">\<workflowInstanceQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6c31-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6c31-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6c31-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c6c31-112">Attributes and elements</span></span>

<span data-ttu-id="c6c31-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c6c31-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6c31-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c6c31-114">Attributes</span></span>  

<span data-ttu-id="c6c31-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="c6c31-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c6c31-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c6c31-116">Child elements</span></span>  
  
|<span data-ttu-id="c6c31-117">Element</span><span class="sxs-lookup"><span data-stu-id="c6c31-117">Element</span></span>|<span data-ttu-id="c6c31-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c6c31-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c31-119">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="c6c31-119">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="c6c31-120">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6c31-120">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6c31-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c6c31-121">Parent elements</span></span>  
  
|<span data-ttu-id="c6c31-122">Element</span><span class="sxs-lookup"><span data-stu-id="c6c31-122">Element</span></span>|<span data-ttu-id="c6c31-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c6c31-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6c31-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="c6c31-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c6c31-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) właściwości.</span><span class="sxs-lookup"><span data-stu-id="c6c31-125">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](https://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6c31-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6c31-126">Remarks</span></span>

<span data-ttu-id="c6c31-127"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="c6c31-127">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="c6c31-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6c31-128">Example</span></span>  

<span data-ttu-id="c6c31-129">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="c6c31-129">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="c6c31-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6c31-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c6c31-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c6c31-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c6c31-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c6c31-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
