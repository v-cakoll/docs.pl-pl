---
title: '&lt;activityScheduledQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 686b58d9efa4420de26fd7be52fe76208af63c6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="f18a9-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f18a9-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="f18a9-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f18a9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="f18a9-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="f18a9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="f18a9-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f18a9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f18a9-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="f18a9-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f18a9-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f18a9-107">\<tracking></span></span>  
<span data-ttu-id="f18a9-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="f18a9-108">\<trackingProfile></span></span>  
<span data-ttu-id="f18a9-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f18a9-109">\<workflow></span></span>  
<span data-ttu-id="f18a9-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="f18a9-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18a9-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="f18a9-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18a9-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f18a9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f18a9-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f18a9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18a9-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f18a9-114">Attributes</span></span>  
 <span data-ttu-id="f18a9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="f18a9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f18a9-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f18a9-116">Child Elements</span></span>  
  
|<span data-ttu-id="f18a9-117">Element</span><span class="sxs-lookup"><span data-stu-id="f18a9-117">Element</span></span>|<span data-ttu-id="f18a9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="f18a9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a9-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="f18a9-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="f18a9-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f18a9-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f18a9-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f18a9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f18a9-122">Element</span><span class="sxs-lookup"><span data-stu-id="f18a9-122">Element</span></span>|<span data-ttu-id="f18a9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f18a9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a9-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f18a9-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f18a9-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f18a9-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f18a9-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f18a9-126">See Also</span></span>  
 <span data-ttu-id="f18a9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f18a9-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="f18a9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f18a9-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="f18a9-129">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="f18a9-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f18a9-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f18a9-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
