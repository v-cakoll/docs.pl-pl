---
title: '&lt;bookmarkResumptionQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: ba8c98557a859f4bd37b9aaca80a44c393429da4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146085"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="9b8d6-102">&lt;bookmarkResumptionQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="9b8d6-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
  
<span data-ttu-id="9b8d6-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9b8d6-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="9b8d6-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9b8d6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="9b8d6-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9b8d6-106">\<system.serviceModel></span></span>  
<span data-ttu-id="9b8d6-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-107">\<tracking></span></span>  
<span data-ttu-id="9b8d6-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-108">\<profiles></span></span>  
<span data-ttu-id="9b8d6-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9b8d6-109">\<trackingProfile></span></span>  
<span data-ttu-id="9b8d6-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-110">\<workflow></span></span>  
<span data-ttu-id="9b8d6-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="9b8d6-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b8d6-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b8d6-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b8d6-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9b8d6-114">Attributes and elements</span></span>  
  
<span data-ttu-id="9b8d6-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b8d6-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9b8d6-116">Attributes</span></span>  
  
<span data-ttu-id="9b8d6-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b8d6-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9b8d6-118">Child elements</span></span>  
  
|<span data-ttu-id="9b8d6-119">Element</span><span class="sxs-lookup"><span data-stu-id="9b8d6-119">Element</span></span>|<span data-ttu-id="9b8d6-120">Opis</span><span class="sxs-lookup"><span data-stu-id="9b8d6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b8d6-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="9b8d6-122">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="9b8d6-123">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b8d6-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9b8d6-124">Parent elements</span></span>  
  
|<span data-ttu-id="9b8d6-125">Element</span><span class="sxs-lookup"><span data-stu-id="9b8d6-125">Element</span></span>|<span data-ttu-id="9b8d6-126">Opis</span><span class="sxs-lookup"><span data-stu-id="9b8d6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b8d6-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9b8d6-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9b8d6-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9b8d6-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b8d6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b8d6-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType> 
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="9b8d6-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9b8d6-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="9b8d6-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9b8d6-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
