---
title: '&lt;activityScheduledQueries&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4fc263f0d70e7c1016bab819fb157dde6fad66d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="6b3be-102">&lt;activityScheduledQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="6b3be-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="6b3be-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b3be-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="6b3be-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="6b3be-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="6b3be-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6b3be-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="6b3be-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6b3be-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6b3be-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="6b3be-107">\<tracking></span></span>  
<span data-ttu-id="6b3be-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6b3be-108">\<trackingProfile></span></span>  
<span data-ttu-id="6b3be-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6b3be-109">\<workflow></span></span>  
<span data-ttu-id="6b3be-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="6b3be-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b3be-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b3be-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b3be-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b3be-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6b3be-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b3be-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b3be-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b3be-114">Attributes</span></span>  
 <span data-ttu-id="6b3be-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="6b3be-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6b3be-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b3be-116">Child Elements</span></span>  
  
|<span data-ttu-id="6b3be-117">Element</span><span class="sxs-lookup"><span data-stu-id="6b3be-117">Element</span></span>|<span data-ttu-id="6b3be-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6b3be-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b3be-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="6b3be-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="6b3be-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b3be-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b3be-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b3be-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6b3be-122">Element</span><span class="sxs-lookup"><span data-stu-id="6b3be-122">Element</span></span>|<span data-ttu-id="6b3be-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6b3be-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b3be-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6b3be-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6b3be-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b3be-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b3be-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b3be-126">See Also</span></span>  
 <span data-ttu-id="6b3be-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="6b3be-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="6b3be-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="6b3be-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="6b3be-129">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="6b3be-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6b3be-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="6b3be-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
