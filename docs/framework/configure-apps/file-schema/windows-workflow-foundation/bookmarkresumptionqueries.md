---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 186990577ec4eedc7cae3710c455816c3162fc94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109412"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="5a51d-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="5a51d-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="5a51d-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5a51d-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5a51d-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="5a51d-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="5a51d-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="5a51d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="5a51d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5a51d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5a51d-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="5a51d-106">\<tracking></span></span>  
<span data-ttu-id="5a51d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5a51d-107">\<trackingProfile></span></span>  
<span data-ttu-id="5a51d-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="5a51d-108">\<workflow></span></span>  
<span data-ttu-id="5a51d-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="5a51d-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="5a51d-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="5a51d-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a51d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a51d-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a51d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a51d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5a51d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a51d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a51d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a51d-114">Attributes</span></span>  
 <span data-ttu-id="5a51d-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="5a51d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a51d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a51d-116">Child Elements</span></span>  
  
|<span data-ttu-id="5a51d-117">Element</span><span class="sxs-lookup"><span data-stu-id="5a51d-117">Element</span></span>|<span data-ttu-id="5a51d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5a51d-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a51d-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="5a51d-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="5a51d-120">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="5a51d-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="5a51d-121">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="5a51d-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a51d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a51d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a51d-123">Element</span><span class="sxs-lookup"><span data-stu-id="5a51d-123">Element</span></span>|<span data-ttu-id="5a51d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="5a51d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a51d-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="5a51d-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="5a51d-126">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5a51d-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a51d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a51d-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="5a51d-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="5a51d-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="5a51d-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="5a51d-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
