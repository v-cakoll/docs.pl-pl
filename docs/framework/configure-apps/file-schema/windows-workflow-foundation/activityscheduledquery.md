---
title: '&lt;activityScheduledQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51db0762c10459d67929867a0fe44908dc7ec750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="b561c-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="b561c-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="b561c-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b561c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b561c-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="b561c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="b561c-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b561c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b561c-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b561c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b561c-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="b561c-107">\<tracking></span></span>  
<span data-ttu-id="b561c-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b561c-108">\<trackingProfile></span></span>  
<span data-ttu-id="b561c-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="b561c-109">\<workflow></span></span>  
<span data-ttu-id="b561c-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="b561c-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="b561c-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b561c-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b561c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="b561c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b561c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b561c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b561c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b561c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b561c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b561c-115">Attributes</span></span>  
  
|<span data-ttu-id="b561c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b561c-116">Attribute</span></span>|<span data-ttu-id="b561c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b561c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b561c-118">activityName</span><span class="sxs-lookup"><span data-stu-id="b561c-118">activityName</span></span>|<span data-ttu-id="b561c-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="b561c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="b561c-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="b561c-120">childActivityName</span></span>|<span data-ttu-id="b561c-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="b561c-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b561c-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b561c-122">Child Elements</span></span>  
 <span data-ttu-id="b561c-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="b561c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b561c-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b561c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b561c-125">Element</span><span class="sxs-lookup"><span data-stu-id="b561c-125">Element</span></span>|<span data-ttu-id="b561c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="b561c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b561c-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="b561c-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="b561c-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b561c-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b561c-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b561c-129">See Also</span></span>  
 <span data-ttu-id="b561c-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b561c-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b561c-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b561c-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b561c-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b561c-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b561c-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="b561c-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
