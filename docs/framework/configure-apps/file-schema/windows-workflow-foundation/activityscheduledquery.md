---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: aa6ee435c66303b5089b459ecc4ed3023297636d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398967"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="710aa-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="710aa-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="710aa-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="710aa-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="710aa-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="710aa-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="710aa-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="710aa-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="710aa-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="710aa-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="710aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="710aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="710aa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="710aa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="710aa-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="710aa-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="710aa-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="710aa-112">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="710aa-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="710aa-113">Attributes and Elements</span></span>  
 <span data-ttu-id="710aa-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="710aa-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="710aa-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="710aa-115">Attributes</span></span>  
  
|<span data-ttu-id="710aa-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="710aa-116">Attribute</span></span>|<span data-ttu-id="710aa-117">Opis</span><span class="sxs-lookup"><span data-stu-id="710aa-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="710aa-118">activityName</span><span class="sxs-lookup"><span data-stu-id="710aa-118">activityName</span></span>|<span data-ttu-id="710aa-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="710aa-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="710aa-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="710aa-120">childActivityName</span></span>|<span data-ttu-id="710aa-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="710aa-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="710aa-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="710aa-122">Child Elements</span></span>  
 <span data-ttu-id="710aa-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="710aa-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="710aa-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="710aa-124">Parent Elements</span></span>  
  
|<span data-ttu-id="710aa-125">Element</span><span class="sxs-lookup"><span data-stu-id="710aa-125">Element</span></span>|<span data-ttu-id="710aa-126">Opis</span><span class="sxs-lookup"><span data-stu-id="710aa-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="710aa-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="710aa-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="710aa-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="710aa-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="710aa-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="710aa-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="710aa-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="710aa-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="710aa-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="710aa-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
