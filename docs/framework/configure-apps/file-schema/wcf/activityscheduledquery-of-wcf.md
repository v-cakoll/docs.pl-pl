---
title: '&lt;activityScheduledQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afb421993c39e66e437a0ecbb35091532df61716
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a><span data-ttu-id="e7148-102">&lt;activityScheduledQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="e7148-102">&lt;activityScheduledQuery&gt; of WCF</span></span>
<span data-ttu-id="e7148-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7148-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e7148-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="e7148-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e7148-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e7148-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="e7148-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e7148-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e7148-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e7148-107">\<tracking></span></span>  
<span data-ttu-id="e7148-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="e7148-108">\<trackingProfile></span></span>  
<span data-ttu-id="e7148-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e7148-109">\<workflow></span></span>  
<span data-ttu-id="e7148-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="e7148-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="e7148-111">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e7148-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7148-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7148-112">Syntax</span></span>  
  
```xml
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7148-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7148-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e7148-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7148-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7148-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7148-115">Attributes</span></span>  
  
|<span data-ttu-id="e7148-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e7148-116">Attribute</span></span>|<span data-ttu-id="e7148-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e7148-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7148-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e7148-118">activityName</span></span>|<span data-ttu-id="e7148-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="e7148-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e7148-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e7148-120">childActivityName</span></span>|<span data-ttu-id="e7148-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="e7148-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7148-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7148-122">Child Elements</span></span>  
 <span data-ttu-id="e7148-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7148-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7148-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7148-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e7148-125">Element</span><span class="sxs-lookup"><span data-stu-id="e7148-125">Element</span></span>|<span data-ttu-id="e7148-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e7148-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7148-127">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="e7148-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e7148-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7148-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7148-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7148-129">See Also</span></span>  
 <span data-ttu-id="e7148-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span><span class="sxs-lookup"><span data-stu-id="e7148-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement></span></span>     
 <span data-ttu-id="e7148-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e7148-131"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="e7148-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e7148-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e7148-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e7148-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
