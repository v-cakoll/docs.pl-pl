---
title: '&lt;bookmarkResumptionQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3240fcf026869aee7540c0e792ccd81e2592e620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbookmarkresumptionquerygt-of-wcf"></a><span data-ttu-id="4b58d-102">&lt;bookmarkResumptionQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="4b58d-102">&lt;bookmarkResumptionQuery&gt; of WCF</span></span>
<span data-ttu-id="4b58d-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4b58d-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="4b58d-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="4b58d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="4b58d-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4b58d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="4b58d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4b58d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4b58d-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="4b58d-107">\<tracking></span></span>  
<span data-ttu-id="4b58d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4b58d-108">\<trackingProfile></span></span>  
<span data-ttu-id="4b58d-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4b58d-109">\<workflow></span></span>  
<span data-ttu-id="4b58d-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="4b58d-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="4b58d-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="4b58d-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b58d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b58d-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4b58d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4b58d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4b58d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4b58d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b58d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4b58d-115">Attributes</span></span>  
  
|<span data-ttu-id="4b58d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4b58d-116">Attribute</span></span>|<span data-ttu-id="4b58d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4b58d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b58d-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="4b58d-118">name</span></span>|<span data-ttu-id="4b58d-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="4b58d-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b58d-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4b58d-120">Child Elements</span></span>  
 <span data-ttu-id="4b58d-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="4b58d-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4b58d-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4b58d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4b58d-123">Element</span><span class="sxs-lookup"><span data-stu-id="4b58d-123">Element</span></span>|<span data-ttu-id="4b58d-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4b58d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b58d-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="4b58d-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="4b58d-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4b58d-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4b58d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b58d-127">See Also</span></span>  
 <span data-ttu-id="4b58d-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4b58d-128"><xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4b58d-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4b58d-129"><xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="4b58d-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4b58d-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4b58d-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4b58d-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
