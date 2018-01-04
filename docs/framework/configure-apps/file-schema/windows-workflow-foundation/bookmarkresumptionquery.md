---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 821ded03ced33ee44c6588daefaf9049741abf8c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="414b3-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="414b3-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="414b3-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="414b3-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="414b3-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="414b3-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="414b3-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="414b3-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="414b3-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="414b3-106">\<system.serviceModel></span></span>  
<span data-ttu-id="414b3-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="414b3-107">\<tracking></span></span>  
<span data-ttu-id="414b3-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="414b3-108">\<trackingProfile></span></span>  
<span data-ttu-id="414b3-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="414b3-109">\<workflow></span></span>  
<span data-ttu-id="414b3-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="414b3-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="414b3-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="414b3-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="414b3-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="414b3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="414b3-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="414b3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="414b3-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="414b3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="414b3-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="414b3-115">Attributes</span></span>  
  
|<span data-ttu-id="414b3-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="414b3-116">Attribute</span></span>|<span data-ttu-id="414b3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="414b3-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="414b3-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="414b3-118">name</span></span>|<span data-ttu-id="414b3-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="414b3-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="414b3-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="414b3-120">Child Elements</span></span>  
 <span data-ttu-id="414b3-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="414b3-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="414b3-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="414b3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="414b3-123">Element</span><span class="sxs-lookup"><span data-stu-id="414b3-123">Element</span></span>|<span data-ttu-id="414b3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="414b3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="414b3-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="414b3-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="414b3-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="414b3-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="414b3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="414b3-127">See Also</span></span>  
 <span data-ttu-id="414b3-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="414b3-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="414b3-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="414b3-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="414b3-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="414b3-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="414b3-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="414b3-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
