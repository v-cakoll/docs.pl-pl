---
title: <bookmarkResumptionQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: ee8457645a0b54e21ef27c2891ebea97d6cc547b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926356"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="7fca4-102">\<bookmarkResumptionQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="7fca4-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="7fca4-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7fca4-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7fca4-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7fca4-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="7fca4-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7fca4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="7fca4-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7fca4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7fca4-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7fca4-107">\<tracking></span></span>  
<span data-ttu-id="7fca4-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="7fca4-108">\<profiles></span></span>  
<span data-ttu-id="7fca4-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7fca4-109">\<trackingProfile></span></span>  
<span data-ttu-id="7fca4-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7fca4-110">\<workflow></span></span>  
<span data-ttu-id="7fca4-111">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7fca4-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7fca4-112">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7fca4-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fca4-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fca4-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7fca4-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7fca4-114">Attributes and elements</span></span>

<span data-ttu-id="7fca4-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7fca4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7fca4-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7fca4-116">Attributes</span></span>  
  
|<span data-ttu-id="7fca4-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7fca4-117">Attribute</span></span>|<span data-ttu-id="7fca4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7fca4-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="7fca4-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="7fca4-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7fca4-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7fca4-120">Child elements</span></span>

<span data-ttu-id="7fca4-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="7fca4-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="7fca4-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7fca4-122">Parent elements</span></span>  
  
|<span data-ttu-id="7fca4-123">Element</span><span class="sxs-lookup"><span data-stu-id="7fca4-123">Element</span></span>|<span data-ttu-id="7fca4-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7fca4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7fca4-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="7fca4-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="7fca4-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7fca4-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7fca4-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7fca4-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7fca4-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7fca4-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7fca4-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7fca4-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
