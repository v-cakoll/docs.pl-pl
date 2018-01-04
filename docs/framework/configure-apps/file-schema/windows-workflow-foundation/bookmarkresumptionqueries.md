---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fb3cf8457dc19081e9eb51091453764513da8ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="b6489-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="b6489-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="b6489-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b6489-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b6489-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="b6489-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="b6489-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b6489-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="b6489-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b6489-106">\<system.serviceModel></span></span>  
<span data-ttu-id="b6489-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="b6489-107">\<tracking></span></span>  
<span data-ttu-id="b6489-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="b6489-108">\<trackingProfile></span></span>  
<span data-ttu-id="b6489-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="b6489-109">\<workflow></span></span>  
<span data-ttu-id="b6489-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="b6489-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="b6489-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="b6489-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6489-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6489-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6489-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6489-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b6489-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6489-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6489-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6489-115">Attributes</span></span>  
 <span data-ttu-id="b6489-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="b6489-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b6489-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6489-117">Child Elements</span></span>  
  
|<span data-ttu-id="b6489-118">Element</span><span class="sxs-lookup"><span data-stu-id="b6489-118">Element</span></span>|<span data-ttu-id="b6489-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b6489-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6489-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="b6489-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="b6489-121">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b6489-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="b6489-122">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="b6489-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6489-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6489-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b6489-124">Element</span><span class="sxs-lookup"><span data-stu-id="b6489-124">Element</span></span>|<span data-ttu-id="b6489-125">Opis</span><span class="sxs-lookup"><span data-stu-id="b6489-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6489-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="b6489-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="b6489-127">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="b6489-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6489-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6489-128">See Also</span></span>  
 <span data-ttu-id="b6489-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b6489-129"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="b6489-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="b6489-130"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="b6489-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b6489-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="b6489-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="b6489-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
