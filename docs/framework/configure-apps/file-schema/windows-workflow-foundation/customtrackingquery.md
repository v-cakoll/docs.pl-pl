---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 4e525bc4c77649a6c6d70ddb2408b6ecce4a0f09
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263771"
---
# <a name="customtrackingquery"></a><span data-ttu-id="75b45-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="75b45-101">\<customTrackingQuery></span></span>
<span data-ttu-id="75b45-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="75b45-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="75b45-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="75b45-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="75b45-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="75b45-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="75b45-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="75b45-105">\<system.serviceModel></span></span>  
<span data-ttu-id="75b45-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="75b45-106">\<tracking></span></span>  
<span data-ttu-id="75b45-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="75b45-107">\<trackingProfile></span></span>  
<span data-ttu-id="75b45-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="75b45-108">\<workflow></span></span>  
<span data-ttu-id="75b45-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="75b45-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="75b45-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="75b45-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b45-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="75b45-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75b45-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="75b45-112">Attributes and Elements</span></span>  
 <span data-ttu-id="75b45-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="75b45-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75b45-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="75b45-114">Attributes</span></span>  
  
|<span data-ttu-id="75b45-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="75b45-115">Attribute</span></span>|<span data-ttu-id="75b45-116">Opis</span><span class="sxs-lookup"><span data-stu-id="75b45-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75b45-117">activityName</span><span class="sxs-lookup"><span data-stu-id="75b45-117">activityName</span></span>|<span data-ttu-id="75b45-118">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="75b45-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="75b45-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="75b45-119">name</span></span>|<span data-ttu-id="75b45-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="75b45-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75b45-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="75b45-121">Child Elements</span></span>  
 <span data-ttu-id="75b45-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="75b45-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75b45-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="75b45-123">Parent Elements</span></span>  
  
|<span data-ttu-id="75b45-124">Element</span><span class="sxs-lookup"><span data-stu-id="75b45-124">Element</span></span>|<span data-ttu-id="75b45-125">Opis</span><span class="sxs-lookup"><span data-stu-id="75b45-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75b45-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="75b45-126">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="75b45-127">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="75b45-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75b45-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75b45-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="75b45-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="75b45-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="75b45-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="75b45-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
