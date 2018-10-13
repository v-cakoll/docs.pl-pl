---
title: '&lt;bookmarkResumptionQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: f0721e7e14d543b1ff212fe59ed6a2de0a8a9968
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308439"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="bfc2f-102">&lt;bookmarkResumptionQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="bfc2f-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>

<span data-ttu-id="bfc2f-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bfc2f-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="bfc2f-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bfc2f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>
  
<span data-ttu-id="bfc2f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="bfc2f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="bfc2f-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-107">\<tracking></span></span>  
<span data-ttu-id="bfc2f-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-108">\<profiles></span></span>  
<span data-ttu-id="bfc2f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="bfc2f-109">\<trackingProfile></span></span>  
<span data-ttu-id="bfc2f-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-110">\<workflow></span></span>  
<span data-ttu-id="bfc2f-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="bfc2f-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc2f-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfc2f-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="bfc2f-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bfc2f-114">Attributes and elements</span></span>

<span data-ttu-id="bfc2f-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfc2f-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bfc2f-116">Attributes</span></span>  
  
|<span data-ttu-id="bfc2f-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bfc2f-117">Attribute</span></span>|<span data-ttu-id="bfc2f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="bfc2f-118">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="bfc2f-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfc2f-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bfc2f-120">Child elements</span></span>

<span data-ttu-id="bfc2f-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-121">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="bfc2f-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bfc2f-122">Parent elements</span></span>  
  
|<span data-ttu-id="bfc2f-123">Element</span><span class="sxs-lookup"><span data-stu-id="bfc2f-123">Element</span></span>|<span data-ttu-id="bfc2f-124">Opis</span><span class="sxs-lookup"><span data-stu-id="bfc2f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfc2f-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="bfc2f-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="bfc2f-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bfc2f-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfc2f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfc2f-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bfc2f-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bfc2f-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bfc2f-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="bfc2f-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
