---
title: '&lt;bookmarkResumptionQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: b0ce29213f1f281e8581b90dda17aba1bdc29072
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltbookmarkresumptionqueriesgt"></a><span data-ttu-id="f7f77-102">&lt;bookmarkResumptionQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="f7f77-102">&lt;bookmarkResumptionQueries&gt;</span></span>
<span data-ttu-id="f7f77-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f7f77-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f7f77-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="f7f77-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="f7f77-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f7f77-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f7f77-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f7f77-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f7f77-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f7f77-107">\<tracking></span></span>  
<span data-ttu-id="f7f77-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f7f77-108">\<trackingProfile></span></span>  
<span data-ttu-id="f7f77-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f7f77-109">\<workflow></span></span>  
<span data-ttu-id="f7f77-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="f7f77-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f7f77-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="f7f77-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f77-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7f77-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7f77-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f7f77-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f7f77-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f7f77-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7f77-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f7f77-115">Attributes</span></span>  
 <span data-ttu-id="f7f77-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f7f77-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f7f77-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f7f77-117">Child Elements</span></span>  
  
|<span data-ttu-id="f7f77-118">Element</span><span class="sxs-lookup"><span data-stu-id="f7f77-118">Element</span></span>|<span data-ttu-id="f7f77-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f7f77-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7f77-120">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="f7f77-120">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="f7f77-121">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f7f77-121">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f7f77-122">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="f7f77-122">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7f77-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f7f77-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f7f77-124">Element</span><span class="sxs-lookup"><span data-stu-id="f7f77-124">Element</span></span>|<span data-ttu-id="f7f77-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f7f77-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7f77-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f7f77-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f7f77-127">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7f77-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f7f77-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7f77-128">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="f7f77-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f7f77-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f7f77-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f7f77-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
