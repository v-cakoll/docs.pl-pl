---
title: '&lt;customTrackingQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9ee5a4a25d379eafb936098597df1ec61ff09f0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725860"
---
# <a name="ltcustomtrackingquerygt"></a><span data-ttu-id="ccfc4-102">&lt;customTrackingQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="ccfc4-102">&lt;customTrackingQuery&gt;</span></span>
<span data-ttu-id="ccfc4-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ccfc4-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ccfc4-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ccfc4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ccfc4-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ccfc4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ccfc4-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ccfc4-107">\<tracking></span></span>  
<span data-ttu-id="ccfc4-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ccfc4-108">\<trackingProfile></span></span>  
<span data-ttu-id="ccfc4-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ccfc4-109">\<workflow></span></span>  
<span data-ttu-id="ccfc4-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="ccfc4-110">\<customTrackingQueries></span></span>  
<span data-ttu-id="ccfc4-111">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ccfc4-111">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccfc4-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ccfc4-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccfc4-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ccfc4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="ccfc4-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccfc4-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ccfc4-115">Attributes</span></span>  
  
|<span data-ttu-id="ccfc4-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ccfc4-116">Attribute</span></span>|<span data-ttu-id="ccfc4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ccfc4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccfc4-118">activityName</span><span class="sxs-lookup"><span data-stu-id="ccfc4-118">activityName</span></span>|<span data-ttu-id="ccfc4-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="ccfc4-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="ccfc4-120">name</span></span>|<span data-ttu-id="ccfc4-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccfc4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ccfc4-122">Child Elements</span></span>  
 <span data-ttu-id="ccfc4-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ccfc4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ccfc4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ccfc4-125">Element</span><span class="sxs-lookup"><span data-stu-id="ccfc4-125">Element</span></span>|<span data-ttu-id="ccfc4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ccfc4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccfc4-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ccfc4-127">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="ccfc4-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ccfc4-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccfc4-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ccfc4-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ccfc4-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ccfc4-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ccfc4-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ccfc4-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
