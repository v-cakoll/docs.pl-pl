---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 7ddf19ed75d50f3cd5f20de8b0e2dfcdd5ea82b0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="f671f-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="f671f-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="f671f-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="f671f-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="f671f-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="f671f-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="f671f-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f671f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f671f-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f671f-106">\<system.serviceModel></span></span>  
<span data-ttu-id="f671f-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f671f-107">\<tracking></span></span>  
<span data-ttu-id="f671f-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f671f-108">\<trackingProfile></span></span>  
<span data-ttu-id="f671f-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f671f-109">\<workflow></span></span>  
<span data-ttu-id="f671f-110">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="f671f-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="f671f-111">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f671f-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f671f-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f671f-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f671f-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f671f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f671f-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f671f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f671f-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f671f-115">Attributes</span></span>  
  
|<span data-ttu-id="f671f-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f671f-116">Attribute</span></span>|<span data-ttu-id="f671f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f671f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f671f-118">activityName</span><span class="sxs-lookup"><span data-stu-id="f671f-118">activityName</span></span>|<span data-ttu-id="f671f-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f671f-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="f671f-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="f671f-120">name</span></span>|<span data-ttu-id="f671f-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="f671f-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f671f-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f671f-122">Child Elements</span></span>  
 <span data-ttu-id="f671f-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="f671f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f671f-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f671f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f671f-125">Element</span><span class="sxs-lookup"><span data-stu-id="f671f-125">Element</span></span>|<span data-ttu-id="f671f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="f671f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f671f-127">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="f671f-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="f671f-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="f671f-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f671f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f671f-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>         
 [<span data-ttu-id="f671f-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f671f-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="f671f-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f671f-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
