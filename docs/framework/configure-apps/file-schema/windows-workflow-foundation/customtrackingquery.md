---
title: '&lt;customTrackingQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 908c340167d50d4d16e0eeff7cc2e01290b55e7a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="d8b06-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="d8b06-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="d8b06-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="d8b06-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="d8b06-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="d8b06-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="d8b06-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d8b06-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d8b06-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d8b06-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d8b06-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d8b06-107">\<tracking></span></span>  
<span data-ttu-id="d8b06-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d8b06-108">\<trackingProfile></span></span>  
<span data-ttu-id="d8b06-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d8b06-109">\<workflow></span></span>  
<span data-ttu-id="d8b06-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="d8b06-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="d8b06-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d8b06-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b06-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8b06-112">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
 </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8b06-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d8b06-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d8b06-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d8b06-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8b06-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d8b06-115">Attributes</span></span>  
  
|<span data-ttu-id="d8b06-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d8b06-116">Attribute</span></span>|<span data-ttu-id="d8b06-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d8b06-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d8b06-118">activityName</span><span class="sxs-lookup"><span data-stu-id="d8b06-118">activityName</span></span>|<span data-ttu-id="d8b06-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d8b06-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="d8b06-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="d8b06-120">name</span></span>|<span data-ttu-id="d8b06-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="d8b06-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8b06-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d8b06-122">Child Elements</span></span>  
 <span data-ttu-id="d8b06-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="d8b06-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8b06-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d8b06-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d8b06-125">Element</span><span class="sxs-lookup"><span data-stu-id="d8b06-125">Element</span></span>|<span data-ttu-id="d8b06-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d8b06-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8b06-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="d8b06-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="d8b06-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="d8b06-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8b06-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8b06-129">See Also</span></span>  
 <span data-ttu-id="d8b06-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d8b06-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d8b06-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d8b06-131"><xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType></span></span>         
 [<span data-ttu-id="d8b06-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="d8b06-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d8b06-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d8b06-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
