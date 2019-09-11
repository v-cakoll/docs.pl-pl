---
title: <workflowInstanceQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 35c73f9d-474e-42eb-874d-ddc04b1987f3
ms.openlocfilehash: eaf0cd204265aac7c1421e3de0c33963e6bbb7a1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854731"
---
# <a name="workflowinstancequery-of-wcf"></a><span data-ttu-id="fd944-102">\<workflowInstanceQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="fd944-102">\<workflowInstanceQuery> of WCF</span></span>

<span data-ttu-id="fd944-103">Reprezentuje zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="fd944-103">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
<span data-ttu-id="fd944-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fd944-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fd944-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fd944-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="fd944-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="fd944-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="fd944-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="fd944-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="fd944-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<workflowInstanceQueries >** ](workflowinstancequeries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="fd944-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries-of-wcf.md)</span></span>\
<span data-ttu-id="fd944-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowInstanceQuery >**</span><span class="sxs-lookup"><span data-stu-id="fd944-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd944-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd944-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd944-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd944-114">Attributes and elements</span></span>  

<span data-ttu-id="fd944-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd944-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd944-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd944-116">Attributes</span></span>  

<span data-ttu-id="fd944-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="fd944-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd944-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd944-118">Child elements</span></span>  
  
|<span data-ttu-id="fd944-119">Element</span><span class="sxs-lookup"><span data-stu-id="fd944-119">Element</span></span>|<span data-ttu-id="fd944-120">Opis</span><span class="sxs-lookup"><span data-stu-id="fd944-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd944-121">\<Stany ></span><span class="sxs-lookup"><span data-stu-id="fd944-121">\<states></span></span>](states-of-wcf-workflowinstancequery.md)|<span data-ttu-id="fd944-122">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fd944-122">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd944-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd944-123">Parent elements</span></span>  
  
|<span data-ttu-id="fd944-124">Element</span><span class="sxs-lookup"><span data-stu-id="fd944-124">Element</span></span>|<span data-ttu-id="fd944-125">Opis</span><span class="sxs-lookup"><span data-stu-id="fd944-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd944-126">\<workflowInstanceQueries></span><span class="sxs-lookup"><span data-stu-id="fd944-126">\<workflowInstanceQueries></span></span>](workflowinstancequeries-of-wcf.md)|<span data-ttu-id="fd944-127">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="fd944-127">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd944-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd944-128">Remarks</span></span>  

<span data-ttu-id="fd944-129"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="fd944-129">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="fd944-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd944-130">Example</span></span>  

<span data-ttu-id="fd944-131">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="fd944-131">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a><span data-ttu-id="fd944-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd944-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fd944-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fd944-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fd944-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="fd944-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
