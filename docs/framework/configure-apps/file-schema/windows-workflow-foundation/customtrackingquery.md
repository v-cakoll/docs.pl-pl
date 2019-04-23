---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 92060260075017359d8a5f0500d52e52c2217d3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076656"
---
# <a name="customtrackingquery"></a><span data-ttu-id="4cafb-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="4cafb-101">\<customTrackingQuery></span></span>
<span data-ttu-id="4cafb-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4cafb-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="4cafb-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="4cafb-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="4cafb-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4cafb-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4cafb-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4cafb-105">\<system.serviceModel></span></span>  
<span data-ttu-id="4cafb-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="4cafb-106">\<tracking></span></span>  
<span data-ttu-id="4cafb-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4cafb-107">\<trackingProfile></span></span>  
<span data-ttu-id="4cafb-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4cafb-108">\<workflow></span></span>  
<span data-ttu-id="4cafb-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="4cafb-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="4cafb-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="4cafb-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cafb-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="4cafb-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4cafb-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4cafb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4cafb-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4cafb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4cafb-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4cafb-114">Attributes</span></span>  
  
|<span data-ttu-id="4cafb-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4cafb-115">Attribute</span></span>|<span data-ttu-id="4cafb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="4cafb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4cafb-117">activityName</span><span class="sxs-lookup"><span data-stu-id="4cafb-117">activityName</span></span>|<span data-ttu-id="4cafb-118">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4cafb-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="4cafb-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="4cafb-119">name</span></span>|<span data-ttu-id="4cafb-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="4cafb-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4cafb-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4cafb-121">Child Elements</span></span>  
 <span data-ttu-id="4cafb-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="4cafb-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4cafb-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4cafb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4cafb-124">Element</span><span class="sxs-lookup"><span data-stu-id="4cafb-124">Element</span></span>|<span data-ttu-id="4cafb-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4cafb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4cafb-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="4cafb-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="4cafb-127">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4cafb-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4cafb-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4cafb-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4cafb-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4cafb-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4cafb-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4cafb-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
