---
title: <workflowInstanceQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: 7e15d7654aeafa5fa7b87922283d6520d5493242
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915223"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="69b3b-102">\<workflowInstanceQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="69b3b-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="69b3b-103">Reprezentuje zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="69b3b-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="69b3b-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="69b3b-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="69b3b-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="69b3b-105">\<system.serviceModel></span></span>  
<span data-ttu-id="69b3b-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="69b3b-106">\<tracking></span></span>  
<span data-ttu-id="69b3b-107">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="69b3b-107">\<profiles></span></span>  
<span data-ttu-id="69b3b-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="69b3b-108">\<trackingProfile></span></span>  
<span data-ttu-id="69b3b-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="69b3b-109">\<workflow></span></span>  
<span data-ttu-id="69b3b-110">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="69b3b-110">\<workflowInstanceQueries></span></span>  
<span data-ttu-id="69b3b-111">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="69b3b-111">\<workflowInstanceQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b3b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="69b3b-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69b3b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69b3b-113">Attributes and elements</span></span>  

<span data-ttu-id="69b3b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69b3b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69b3b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69b3b-115">Attributes</span></span>  

<span data-ttu-id="69b3b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="69b3b-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69b3b-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69b3b-117">Child elements</span></span>  
  
|<span data-ttu-id="69b3b-118">Element</span><span class="sxs-lookup"><span data-stu-id="69b3b-118">Element</span></span>|<span data-ttu-id="69b3b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="69b3b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69b3b-120">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="69b3b-120">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="69b3b-121">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="69b3b-121">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69b3b-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69b3b-122">Parent elements</span></span>  
  
|<span data-ttu-id="69b3b-123">Element</span><span class="sxs-lookup"><span data-stu-id="69b3b-123">Element</span></span>|<span data-ttu-id="69b3b-124">Opis</span><span class="sxs-lookup"><span data-stu-id="69b3b-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69b3b-125">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="69b3b-125">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="69b3b-126">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="69b3b-126">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69b3b-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69b3b-127">Remarks</span></span>  

<span data-ttu-id="69b3b-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="69b3b-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="69b3b-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="69b3b-129">Example</span></span>  

<span data-ttu-id="69b3b-130">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="69b3b-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="69b3b-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69b3b-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="69b3b-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="69b3b-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="69b3b-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="69b3b-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
