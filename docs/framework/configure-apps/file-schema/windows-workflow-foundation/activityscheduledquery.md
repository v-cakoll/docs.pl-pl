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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 779ac3995d4d5fb1b63de6ae6b9db7103691d6f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="6810b-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="6810b-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="6810b-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6810b-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="6810b-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="6810b-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="6810b-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6810b-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6810b-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6810b-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6810b-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="6810b-107">\<tracking></span></span>  
<span data-ttu-id="6810b-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6810b-108">\<trackingProfile></span></span>  
<span data-ttu-id="6810b-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6810b-109">\<workflow></span></span>  
<span data-ttu-id="6810b-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="6810b-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="6810b-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="6810b-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6810b-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="6810b-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6810b-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6810b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6810b-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6810b-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6810b-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6810b-115">Attributes</span></span>  
  
|<span data-ttu-id="6810b-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6810b-116">Attribute</span></span>|<span data-ttu-id="6810b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6810b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6810b-118">activityName</span><span class="sxs-lookup"><span data-stu-id="6810b-118">activityName</span></span>|<span data-ttu-id="6810b-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="6810b-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="6810b-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="6810b-120">childActivityName</span></span>|<span data-ttu-id="6810b-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="6810b-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6810b-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6810b-122">Child Elements</span></span>  
 <span data-ttu-id="6810b-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="6810b-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6810b-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6810b-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6810b-125">Element</span><span class="sxs-lookup"><span data-stu-id="6810b-125">Element</span></span>|<span data-ttu-id="6810b-126">Opis</span><span class="sxs-lookup"><span data-stu-id="6810b-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6810b-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="6810b-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="6810b-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6810b-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6810b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6810b-129">See Also</span></span>  
 <span data-ttu-id="6810b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6810b-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="6810b-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="6810b-131"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="6810b-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="6810b-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6810b-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="6810b-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
