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
ms.workload: dotnet
ms.openlocfilehash: 5a857a86d45226e3dd3805a900612f55078c0bf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="2f777-102">&lt;activityScheduledQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="2f777-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="2f777-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f777-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="2f777-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="2f777-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="2f777-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="2f777-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="2f777-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2f777-106">\<system.serviceModel></span></span>  
<span data-ttu-id="2f777-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2f777-107">\<tracking></span></span>  
<span data-ttu-id="2f777-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="2f777-108">\<trackingProfile></span></span>  
<span data-ttu-id="2f777-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2f777-109">\<workflow></span></span>  
<span data-ttu-id="2f777-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="2f777-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f777-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f777-111">Syntax</span></span>  
  
```xml  
<tracking>     <trackingProfile name="Name">       <workflow>          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>       </workflow>     </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f777-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2f777-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2f777-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f777-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f777-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2f777-114">Attributes</span></span>  
 <span data-ttu-id="2f777-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="2f777-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2f777-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2f777-116">Child Elements</span></span>  
  
|<span data-ttu-id="2f777-117">Element</span><span class="sxs-lookup"><span data-stu-id="2f777-117">Element</span></span>|<span data-ttu-id="2f777-118">Opis</span><span class="sxs-lookup"><span data-stu-id="2f777-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f777-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="2f777-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="2f777-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f777-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f777-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2f777-121">Parent Elements</span></span>  
  
|<span data-ttu-id="2f777-122">Element</span><span class="sxs-lookup"><span data-stu-id="2f777-122">Element</span></span>|<span data-ttu-id="2f777-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2f777-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f777-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2f777-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2f777-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="2f777-125">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f777-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f777-126">See Also</span></span>  
 <span data-ttu-id="2f777-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="2f777-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection></span></span>     
 <span data-ttu-id="2f777-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="2f777-128"><xref:System.Activities.Tracking.ActivityScheduledQuery></span></span>     
 [<span data-ttu-id="2f777-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2f777-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="2f777-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2f777-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
