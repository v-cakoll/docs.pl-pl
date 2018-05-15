---
title: '&lt;customTrackingQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: ed29ff039cd7fd4eb0acccea1b0adf8995c3e1f3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="ae88a-102">&lt;customTrackingQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="ae88a-102">&lt;customTrackingQuery&gt; of WCF</span></span>
<span data-ttu-id="ae88a-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ae88a-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ae88a-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="ae88a-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ae88a-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ae88a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="ae88a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae88a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ae88a-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ae88a-107">\<tracking></span></span>  
<span data-ttu-id="ae88a-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ae88a-108">\<trackingProfile></span></span>  
<span data-ttu-id="ae88a-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ae88a-109">\<workflow></span></span>  
<span data-ttu-id="ae88a-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="ae88a-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="ae88a-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="ae88a-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae88a-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae88a-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae88a-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae88a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ae88a-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae88a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae88a-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae88a-115">Attributes</span></span>  
  
|<span data-ttu-id="ae88a-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ae88a-116">Attribute</span></span>|<span data-ttu-id="ae88a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ae88a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae88a-118">activityName</span><span class="sxs-lookup"><span data-stu-id="ae88a-118">activityName</span></span>|<span data-ttu-id="ae88a-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ae88a-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="ae88a-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="ae88a-120">name</span></span>|<span data-ttu-id="ae88a-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="ae88a-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae88a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae88a-122">Child Elements</span></span>  
 <span data-ttu-id="ae88a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae88a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae88a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae88a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ae88a-125">Element</span><span class="sxs-lookup"><span data-stu-id="ae88a-125">Element</span></span>|<span data-ttu-id="ae88a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ae88a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae88a-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="ae88a-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ae88a-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ae88a-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae88a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae88a-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>      
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="ae88a-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ae88a-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="ae88a-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ae88a-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
