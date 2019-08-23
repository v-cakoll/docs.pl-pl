---
title: <bookmarkResumptionQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 5ec9827e9862866096265da576c91b10573012d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919742"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="96216-102">\<bookmarkResumptionQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="96216-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="96216-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96216-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="96216-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="96216-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="96216-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="96216-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="96216-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96216-106">\<system.serviceModel></span></span>  
<span data-ttu-id="96216-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="96216-107">\<tracking></span></span>  
<span data-ttu-id="96216-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="96216-108">\<profiles></span></span>  
<span data-ttu-id="96216-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="96216-109">\<trackingProfile></span></span>  
<span data-ttu-id="96216-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="96216-110">\<workflow></span></span>  
<span data-ttu-id="96216-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="96216-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="96216-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="96216-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96216-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="96216-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96216-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="96216-114">Attributes and elements</span></span>  
  
<span data-ttu-id="96216-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="96216-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96216-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96216-116">Attributes</span></span>  
  
<span data-ttu-id="96216-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="96216-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96216-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="96216-118">Child elements</span></span>  
  
|<span data-ttu-id="96216-119">Element</span><span class="sxs-lookup"><span data-stu-id="96216-119">Element</span></span>|<span data-ttu-id="96216-120">Opis</span><span class="sxs-lookup"><span data-stu-id="96216-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96216-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="96216-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="96216-122">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="96216-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="96216-123">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="96216-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96216-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="96216-124">Parent elements</span></span>  
  
|<span data-ttu-id="96216-125">Element</span><span class="sxs-lookup"><span data-stu-id="96216-125">Element</span></span>|<span data-ttu-id="96216-126">Opis</span><span class="sxs-lookup"><span data-stu-id="96216-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96216-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="96216-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="96216-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="96216-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96216-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96216-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="96216-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96216-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="96216-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="96216-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
