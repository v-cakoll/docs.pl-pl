---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 4277df5b4c36fa2f3571ba8441a7eb8aaf6d106a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261555"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="3ac9e-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="3ac9e-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="3ac9e-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3ac9e-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="3ac9e-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3ac9e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3ac9e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3ac9e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3ac9e-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="3ac9e-106">\<tracking></span></span>  
<span data-ttu-id="3ac9e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3ac9e-107">\<trackingProfile></span></span>  
<span data-ttu-id="3ac9e-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="3ac9e-108">\<workflow></span></span>  
<span data-ttu-id="3ac9e-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="3ac9e-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="3ac9e-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="3ac9e-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac9e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ac9e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ac9e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ac9e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3ac9e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ac9e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ac9e-114">Attributes</span></span>  
 <span data-ttu-id="3ac9e-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3ac9e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ac9e-116">Child Elements</span></span>  
  
|<span data-ttu-id="3ac9e-117">Element</span><span class="sxs-lookup"><span data-stu-id="3ac9e-117">Element</span></span>|<span data-ttu-id="3ac9e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac9e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ac9e-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="3ac9e-119">\<bookmarkResumptionQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionquery.md)|<span data-ttu-id="3ac9e-120">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="3ac9e-121">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ac9e-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ac9e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3ac9e-123">Element</span><span class="sxs-lookup"><span data-stu-id="3ac9e-123">Element</span></span>|<span data-ttu-id="3ac9e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="3ac9e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ac9e-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="3ac9e-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="3ac9e-126">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="3ac9e-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ac9e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ac9e-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3ac9e-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3ac9e-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3ac9e-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="3ac9e-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
