---
title: '&lt;bookmarkResumptionQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: d2b3365f3793c114003bbd9b9da664448bbac243
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147655"
---
# <a name="ltbookmarkresumptionqueriesgt-of-wcf"></a><span data-ttu-id="7840f-102">&lt;bookmarkResumptionQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="7840f-102">&lt;bookmarkResumptionQueries&gt; of WCF</span></span>

<span data-ttu-id="7840f-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7840f-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7840f-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7840f-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="7840f-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7840f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="7840f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7840f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7840f-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7840f-107">\<tracking></span></span>  
<span data-ttu-id="7840f-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="7840f-108">\<profiles></span></span>  
<span data-ttu-id="7840f-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7840f-109">\<trackingProfile></span></span>  
<span data-ttu-id="7840f-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7840f-110">\<workflow></span></span>  
<span data-ttu-id="7840f-111">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="7840f-111">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7840f-112">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7840f-112">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7840f-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="7840f-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="7840f-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7840f-114">Attributes and elements</span></span>

<span data-ttu-id="7840f-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7840f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7840f-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7840f-116">Attributes</span></span>

<span data-ttu-id="7840f-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="7840f-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7840f-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7840f-118">Child elements</span></span>  
  
|<span data-ttu-id="7840f-119">Element</span><span class="sxs-lookup"><span data-stu-id="7840f-119">Element</span></span>|<span data-ttu-id="7840f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="7840f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7840f-121">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="7840f-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="7840f-122">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7840f-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7840f-123">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7840f-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7840f-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7840f-124">Parent elements</span></span>  
  
|<span data-ttu-id="7840f-125">Element</span><span class="sxs-lookup"><span data-stu-id="7840f-125">Element</span></span>|<span data-ttu-id="7840f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7840f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7840f-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7840f-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7840f-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="7840f-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7840f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7840f-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType> 
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="7840f-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7840f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="7840f-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7840f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
