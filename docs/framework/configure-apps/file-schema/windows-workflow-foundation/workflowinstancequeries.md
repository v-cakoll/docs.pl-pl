---
title: <workflowInstanceQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fe7ce85-cf9a-4dbf-a8f7-bc9b1fc2fe35
ms.openlocfilehash: 11e301de1ab3dbd4c97f236bfd07c5de4a632272
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398575"
---
# <a name="workflowinstancequeries"></a><span data-ttu-id="5d771-101">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="5d771-101">\<workflowInstanceQueries></span></span>
<span data-ttu-id="5d771-102">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="5d771-102">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="5d771-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5d771-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5d771-105">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="5d771-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="5d771-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="5d771-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5d771-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="5d771-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQueries >**</span><span class="sxs-lookup"><span data-stu-id="5d771-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d771-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d771-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d771-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5d771-111">Attributes and Elements</span></span>  

<span data-ttu-id="5d771-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5d771-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d771-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5d771-113">Attributes</span></span>  

<span data-ttu-id="5d771-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="5d771-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5d771-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5d771-115">Child Elements</span></span>  
  
|<span data-ttu-id="5d771-116">Element</span><span class="sxs-lookup"><span data-stu-id="5d771-116">Element</span></span>|<span data-ttu-id="5d771-117">Opis</span><span class="sxs-lookup"><span data-stu-id="5d771-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d771-118">\<workflowInstanceQuery></span><span class="sxs-lookup"><span data-stu-id="5d771-118">\<workflowInstanceQuery></span></span>](workflowinstancequery.md)|<span data-ttu-id="5d771-119">Zapytanie, które jest używane do śledzenia zmian cyklem życia wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5d771-119">A query that is used to track workflow instance life cycle changes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5d771-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5d771-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5d771-121">Element</span><span class="sxs-lookup"><span data-stu-id="5d771-121">Element</span></span>|<span data-ttu-id="5d771-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5d771-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d771-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="5d771-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="5d771-124">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="5d771-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d771-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d771-125">Remarks</span></span>  

<span data-ttu-id="5d771-126"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="5d771-126">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="5d771-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d771-127">Example</span></span>  

<span data-ttu-id="5d771-128">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="5d771-128">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5d771-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d771-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5d771-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5d771-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5d771-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5d771-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
