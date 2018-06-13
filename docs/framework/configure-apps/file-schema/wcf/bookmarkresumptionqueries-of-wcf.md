---
title: '&lt;bookmarkResumptionQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 8a83f521e444838b6495221c00211710dd99ab6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753043"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="10f1d-102">&lt;bookmarkResumptionQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="10f1d-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>
<span data-ttu-id="10f1d-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="10f1d-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="10f1d-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="10f1d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="10f1d-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="10f1d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="10f1d-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="10f1d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="10f1d-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="10f1d-107">\<tracking></span></span>  
<span data-ttu-id="10f1d-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="10f1d-108">\<trackingProfile></span></span>  
<span data-ttu-id="10f1d-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="10f1d-109">\<workflow></span></span>  
<span data-ttu-id="10f1d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="10f1d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="10f1d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="10f1d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10f1d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="10f1d-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="10f1d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="10f1d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="10f1d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="10f1d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10f1d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="10f1d-115">Attributes</span></span>  
 <span data-ttu-id="10f1d-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="10f1d-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10f1d-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="10f1d-117">Child Elements</span></span>  
  
|<span data-ttu-id="10f1d-118">Element</span><span class="sxs-lookup"><span data-stu-id="10f1d-118">Element</span></span>|<span data-ttu-id="10f1d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="10f1d-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10f1d-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="10f1d-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="10f1d-121">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="10f1d-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="10f1d-122">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="10f1d-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10f1d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="10f1d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="10f1d-124">Element</span><span class="sxs-lookup"><span data-stu-id="10f1d-124">Element</span></span>|<span data-ttu-id="10f1d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="10f1d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10f1d-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="10f1d-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="10f1d-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="10f1d-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10f1d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10f1d-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="10f1d-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="10f1d-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="10f1d-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="10f1d-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
