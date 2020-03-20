---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 09cbc43ae4db82dc80e6985131f8d6cc0c24b2ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152414"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="e3ab0-101">\<działalnośćScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e3ab0-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="e3ab0-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e3ab0-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e3ab0-104">Aby uzyskać więcej informacji na temat śledzenia zapytań profilowych, zobacz [Śledzenie profili](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e3ab0-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e3ab0-106">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="e3ab0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="e3ab0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="e3ab0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="e3ab0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span><span class="sxs-lookup"><span data-stu-id="e3ab0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries.md)</span></span>\
<span data-ttu-id="e3ab0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<działalnośćScheduledQuery>**</span><span class="sxs-lookup"><span data-stu-id="e3ab0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3ab0-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3ab0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3ab0-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3ab0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e3ab0-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3ab0-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3ab0-115">Attributes</span></span>  
  
|<span data-ttu-id="e3ab0-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e3ab0-116">Attribute</span></span>|<span data-ttu-id="e3ab0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ab0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3ab0-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e3ab0-118">activityName</span></span>|<span data-ttu-id="e3ab0-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e3ab0-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e3ab0-120">childActivityName</span></span>|<span data-ttu-id="e3ab0-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3ab0-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3ab0-122">Child Elements</span></span>  
 <span data-ttu-id="e3ab0-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3ab0-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3ab0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e3ab0-125">Element</span><span class="sxs-lookup"><span data-stu-id="e3ab0-125">Element</span></span>|<span data-ttu-id="e3ab0-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ab0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3ab0-127">\<działalnośćScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e3ab0-127">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="e3ab0-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3ab0-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3ab0-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3ab0-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e3ab0-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e3ab0-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e3ab0-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e3ab0-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
