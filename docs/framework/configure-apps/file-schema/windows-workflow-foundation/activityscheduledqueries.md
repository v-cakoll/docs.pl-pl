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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 048b141d54a0fded8e3a5771c0f6c37bef9f7e30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltactivityscheduledqueriesgt"></a><span data-ttu-id="468dd-102">&lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="468dd-102">&lt;activityScheduledQueries&gt;</span></span>
<span data-ttu-id="468dd-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="468dd-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="468dd-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="468dd-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="468dd-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="468dd-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="468dd-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="468dd-106">\<system.serviceModel></span></span>  
<span data-ttu-id="468dd-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="468dd-107">\<tracking></span></span>  
<span data-ttu-id="468dd-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="468dd-108">\<trackingProfile></span></span>  
<span data-ttu-id="468dd-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="468dd-109">\<workflow></span></span>  
<span data-ttu-id="468dd-110">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="468dd-110">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="468dd-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="468dd-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="468dd-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="468dd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="468dd-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="468dd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="468dd-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="468dd-114">Attributes</span></span>  
 <span data-ttu-id="468dd-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="468dd-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="468dd-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="468dd-116">Child Elements</span></span>  
  
|<span data-ttu-id="468dd-117">Element</span><span class="sxs-lookup"><span data-stu-id="468dd-117">Element</span></span>|<span data-ttu-id="468dd-118">Opis</span><span class="sxs-lookup"><span data-stu-id="468dd-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="468dd-119">\<activityScheduledQuery ></span><span class="sxs-lookup"><span data-stu-id="468dd-119">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="468dd-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="468dd-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="468dd-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="468dd-121">Parent Elements</span></span>  
  
|<span data-ttu-id="468dd-122">Element</span><span class="sxs-lookup"><span data-stu-id="468dd-122">Element</span></span>|<span data-ttu-id="468dd-123">Opis</span><span class="sxs-lookup"><span data-stu-id="468dd-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="468dd-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="468dd-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="468dd-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="468dd-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="468dd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="468dd-126">See Also</span></span>  
 <span data-ttu-id="468dd-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="468dd-127"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="468dd-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="468dd-128"><xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="468dd-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="468dd-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="468dd-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="468dd-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
