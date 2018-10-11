---
title: '&lt;bookmarkResumptionQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 07215347da19a05d5915296668d990853fdae646
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087794"
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="8100e-102">&lt;bookmarkResumptionQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="8100e-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="8100e-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8100e-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="8100e-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="8100e-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="8100e-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8100e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8100e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8100e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8100e-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8100e-107">\<tracking></span></span>  
<span data-ttu-id="8100e-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8100e-108">\<trackingProfile></span></span>  
<span data-ttu-id="8100e-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8100e-109">\<workflow></span></span>  
<span data-ttu-id="8100e-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="8100e-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="8100e-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="8100e-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8100e-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="8100e-112">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="8100e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8100e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8100e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8100e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8100e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8100e-115">Attributes</span></span>  
  
|<span data-ttu-id="8100e-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8100e-116">Attribute</span></span>|<span data-ttu-id="8100e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8100e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8100e-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="8100e-118">name</span></span>|<span data-ttu-id="8100e-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="8100e-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8100e-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8100e-120">Child Elements</span></span>  
 <span data-ttu-id="8100e-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="8100e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8100e-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8100e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8100e-123">Element</span><span class="sxs-lookup"><span data-stu-id="8100e-123">Element</span></span>|<span data-ttu-id="8100e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="8100e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8100e-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="8100e-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="8100e-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8100e-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8100e-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8100e-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="8100e-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8100e-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8100e-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8100e-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
