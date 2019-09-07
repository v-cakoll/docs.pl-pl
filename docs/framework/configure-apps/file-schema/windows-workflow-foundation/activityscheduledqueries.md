---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: a43242e2f22c48a57c11f6f03657d7d3de27ff48
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398981"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="fe8aa-101">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="fe8aa-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="fe8aa-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe8aa-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="fe8aa-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="fe8aa-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="fe8aa-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="fe8aa-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe8aa-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fe8aa-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="fe8aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="fe8aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fe8aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="fe8aa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="fe8aa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8aa-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe8aa-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe8aa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fe8aa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fe8aa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe8aa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe8aa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fe8aa-114">Attributes</span></span>  
 <span data-ttu-id="fe8aa-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="fe8aa-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fe8aa-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fe8aa-116">Child Elements</span></span>  
  
|<span data-ttu-id="fe8aa-117">Element</span><span class="sxs-lookup"><span data-stu-id="fe8aa-117">Element</span></span>|<span data-ttu-id="fe8aa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="fe8aa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe8aa-119">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="fe8aa-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="fe8aa-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fe8aa-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe8aa-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fe8aa-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fe8aa-122">Element</span><span class="sxs-lookup"><span data-stu-id="fe8aa-122">Element</span></span>|<span data-ttu-id="fe8aa-123">Opis</span><span class="sxs-lookup"><span data-stu-id="fe8aa-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe8aa-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="fe8aa-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="fe8aa-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="fe8aa-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe8aa-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe8aa-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="fe8aa-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="fe8aa-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fe8aa-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="fe8aa-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
