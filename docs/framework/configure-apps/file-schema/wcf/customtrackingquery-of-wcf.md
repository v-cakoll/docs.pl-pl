---
title: '&lt;customTrackingQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27637abceb23a54e784afbcc2e0517db51542b53
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="8db9d-102">&lt;customTrackingQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="8db9d-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="8db9d-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="8db9d-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8db9d-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="8db9d-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8db9d-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8db9d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="8db9d-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="8db9d-106">\<system.serviceModel></span></span>  
<span data-ttu-id="8db9d-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8db9d-107">\<tracking></span></span>  
<span data-ttu-id="8db9d-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="8db9d-108">\<trackingProfile></span></span>  
<span data-ttu-id="8db9d-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8db9d-109">\<workflow></span></span>  
<span data-ttu-id="8db9d-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="8db9d-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="8db9d-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8db9d-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db9d-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="8db9d-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8db9d-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8db9d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8db9d-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8db9d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8db9d-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8db9d-115">Attributes</span></span>  
  
|<span data-ttu-id="8db9d-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8db9d-116">Attribute</span></span>|<span data-ttu-id="8db9d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8db9d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8db9d-118">activityName</span><span class="sxs-lookup"><span data-stu-id="8db9d-118">activityName</span></span>|<span data-ttu-id="8db9d-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="8db9d-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="8db9d-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="8db9d-120">name</span></span>|<span data-ttu-id="8db9d-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="8db9d-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8db9d-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8db9d-122">Child Elements</span></span>  
 <span data-ttu-id="8db9d-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="8db9d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8db9d-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8db9d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8db9d-125">Element</span><span class="sxs-lookup"><span data-stu-id="8db9d-125">Element</span></span>|<span data-ttu-id="8db9d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="8db9d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8db9d-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="8db9d-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="8db9d-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="8db9d-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8db9d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8db9d-129">See Also</span></span>  
 <span data-ttu-id="8db9d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8db9d-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>      
 <span data-ttu-id="8db9d-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8db9d-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="8db9d-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8db9d-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="8db9d-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8db9d-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
