---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: f048612673a9b6b69c3cdded6526c76359c444e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945987"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="bdc13-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="bdc13-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="bdc13-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bdc13-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bdc13-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="bdc13-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="bdc13-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bdc13-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="bdc13-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bdc13-105">\<system.serviceModel></span></span>  
<span data-ttu-id="bdc13-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="bdc13-106">\<tracking></span></span>  
<span data-ttu-id="bdc13-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bdc13-107">\<trackingProfile></span></span>  
<span data-ttu-id="bdc13-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="bdc13-108">\<workflow></span></span>  
<span data-ttu-id="bdc13-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="bdc13-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="bdc13-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="bdc13-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc13-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdc13-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdc13-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bdc13-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bdc13-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bdc13-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdc13-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bdc13-114">Attributes</span></span>  
 <span data-ttu-id="bdc13-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="bdc13-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bdc13-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bdc13-116">Child Elements</span></span>  
  
|<span data-ttu-id="bdc13-117">Element</span><span class="sxs-lookup"><span data-stu-id="bdc13-117">Element</span></span>|<span data-ttu-id="bdc13-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bdc13-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdc13-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="bdc13-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="bdc13-120">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bdc13-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bdc13-121">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="bdc13-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bdc13-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bdc13-122">Parent Elements</span></span>  
  
|<span data-ttu-id="bdc13-123">Element</span><span class="sxs-lookup"><span data-stu-id="bdc13-123">Element</span></span>|<span data-ttu-id="bdc13-124">Opis</span><span class="sxs-lookup"><span data-stu-id="bdc13-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bdc13-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="bdc13-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="bdc13-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="bdc13-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bdc13-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdc13-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bdc13-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bdc13-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bdc13-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="bdc13-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
