---
title: <workflowInstanceQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 9096e812-626a-409a-9eda-c31a60b84c55
ms.openlocfilehash: 68e44584858e55c136bc3c3dc5f1fb333485fa17
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397514"
---
# \<workflowInstanceQuery>
<span data-ttu-id="3c633-101">Reprezentuje zapytanie, które śledzi zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="3c633-101">Represents a query that tracks workflow instance life cycle changes such as a started or completed event.</span></span>  
  
 <span data-ttu-id="3c633-102">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3c633-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowInstanceQueries>**](workflowinstancequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowInstanceQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="3c633-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c633-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c633-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3c633-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3c633-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3c633-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c633-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3c633-106">Attributes</span></span>  
 <span data-ttu-id="3c633-107">Brak.</span><span class="sxs-lookup"><span data-stu-id="3c633-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c633-108">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3c633-108">Child Elements</span></span>  
  
|<span data-ttu-id="3c633-109">Element</span><span class="sxs-lookup"><span data-stu-id="3c633-109">Element</span></span>|<span data-ttu-id="3c633-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3c633-110">Description</span></span>|  
|-------------|-----------------|  
|[\<states>](states.md)|<span data-ttu-id="3c633-111">Kolekcja subskrybowanego stanów z wystąpienia elementu śledzonych przepływu pracy podczas tworzenia rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3c633-111">A collection of subscribed states from the tracked workflow instance when the tracking records are created.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c633-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3c633-112">Parent Elements</span></span>  
  
|<span data-ttu-id="3c633-113">Element</span><span class="sxs-lookup"><span data-stu-id="3c633-113">Element</span></span>|<span data-ttu-id="3c633-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3c633-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowInstanceQueries>](workflowinstancequeries.md)|<span data-ttu-id="3c633-115">Reprezentuje kolekcję elementów konfiguracji, które śledzą zmiany cyklu życia wystąpienia przepływu pracy, takie jak zdarzenie uruchomione lub ukończone.</span><span class="sxs-lookup"><span data-stu-id="3c633-115">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c633-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c633-116">Remarks</span></span>  
 <span data-ttu-id="3c633-117"><xref:System.Activities.Tracking.WorkflowInstanceQuery> Jest używana do subskrybowania następujących <xref:System.Activities.Tracking.TrackingRecord> obiektów:</span><span class="sxs-lookup"><span data-stu-id="3c633-117">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>  
  
- <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>  
  
## <a name="example"></a><span data-ttu-id="3c633-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c633-118">Example</span></span>  
 <span data-ttu-id="3c633-119">Następująca konfiguracja subskrybuje przepływu rekordów dla śledzenia na poziomie wystąpienia `Started` stan wystąpienia przy użyciu tego zapytania.</span><span class="sxs-lookup"><span data-stu-id="3c633-119">The following configuration subscribes to workflow instance-level tracking records for the `Started` instance state using this query.</span></span>  
  
```xml  
<workflowInstanceQueries>  
    <workflowInstanceQuery>  
      <states>  
        <state name="Started"/>  
      </states>  
    </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c633-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c633-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3c633-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3c633-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3c633-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="3c633-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
