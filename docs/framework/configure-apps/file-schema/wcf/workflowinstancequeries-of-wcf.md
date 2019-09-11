---
title: <workflowInstanceQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: b0852f77-16e4-4d55-8eb7-a19feb0e8fc4
ms.openlocfilehash: 8a58767745efab67fb7550de8770fec2c6226117
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854769"
---
# <a name="workflowinstancequeries-of-wcf"></a><span data-ttu-id="4ccc3-102">\<workflowInstanceQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="4ccc3-102">\<workflowInstanceQueries> of WCF</span></span>

<span data-ttu-id="4ccc3-103">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="4ccc3-103">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="4ccc3-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4ccc3-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4ccc3-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4ccc3-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="4ccc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="4ccc3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="4ccc3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="4ccc3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4ccc3-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="4ccc3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="4ccc3-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ccc3-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ccc3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ccc3-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4ccc3-113">Attributes and elements</span></span>

<span data-ttu-id="4ccc3-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4ccc3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ccc3-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4ccc3-115">Attributes</span></span>  

<span data-ttu-id="4ccc3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="4ccc3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4ccc3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4ccc3-117">Child elements</span></span>  
  
|<span data-ttu-id="4ccc3-118">Element</span><span class="sxs-lookup"><span data-stu-id="4ccc3-118">Element</span></span>|<span data-ttu-id="4ccc3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4ccc3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ccc3-120">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="4ccc3-120">\<workflowInstanceQuery></span></span>](workflowinstancequery-of-wcf.md)|<span data-ttu-id="4ccc3-121">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4ccc3-121">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4ccc3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4ccc3-122">Parent elements</span></span>  
  
|<span data-ttu-id="4ccc3-123">Element</span><span class="sxs-lookup"><span data-stu-id="4ccc3-123">Element</span></span>|<span data-ttu-id="4ccc3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4ccc3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ccc3-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4ccc3-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="4ccc3-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) .</span><span class="sxs-lookup"><span data-stu-id="4ccc3-126">A configuration element that contains all queries for a specific workflow identified by the [activityDefinitionId](xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId) property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ccc3-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4ccc3-127">Remarks</span></span>

<span data-ttu-id="4ccc3-128"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="4ccc3-128">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="4ccc3-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="4ccc3-129">Example</span></span>  

<span data-ttu-id="4ccc3-130">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="4ccc3-130">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="4ccc3-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ccc3-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4ccc3-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4ccc3-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4ccc3-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4ccc3-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
