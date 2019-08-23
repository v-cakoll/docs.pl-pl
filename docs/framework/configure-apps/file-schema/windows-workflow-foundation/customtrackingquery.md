---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 9605f5d050baf046ff3c549c19191934299a65e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945754"
---
# <a name="customtrackingquery"></a><span data-ttu-id="73203-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="73203-101">\<customTrackingQuery></span></span>
<span data-ttu-id="73203-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="73203-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="73203-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="73203-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="73203-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="73203-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="73203-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73203-105">\<system.serviceModel></span></span>  
<span data-ttu-id="73203-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="73203-106">\<tracking></span></span>  
<span data-ttu-id="73203-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="73203-107">\<trackingProfile></span></span>  
<span data-ttu-id="73203-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="73203-108">\<workflow></span></span>  
<span data-ttu-id="73203-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="73203-109">\<customTrackingQueries></span></span>  
<span data-ttu-id="73203-110">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="73203-110">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73203-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="73203-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73203-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73203-112">Attributes and Elements</span></span>  
 <span data-ttu-id="73203-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73203-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73203-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73203-114">Attributes</span></span>  
  
|<span data-ttu-id="73203-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="73203-115">Attribute</span></span>|<span data-ttu-id="73203-116">Opis</span><span class="sxs-lookup"><span data-stu-id="73203-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73203-117">activityName</span><span class="sxs-lookup"><span data-stu-id="73203-117">activityName</span></span>|<span data-ttu-id="73203-118">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="73203-118">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="73203-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="73203-119">name</span></span>|<span data-ttu-id="73203-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="73203-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73203-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73203-121">Child Elements</span></span>  
 <span data-ttu-id="73203-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="73203-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73203-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73203-123">Parent Elements</span></span>  
  
|<span data-ttu-id="73203-124">Element</span><span class="sxs-lookup"><span data-stu-id="73203-124">Element</span></span>|<span data-ttu-id="73203-125">Opis</span><span class="sxs-lookup"><span data-stu-id="73203-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73203-126">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="73203-126">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="73203-127">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="73203-127">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73203-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73203-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="73203-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="73203-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="73203-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="73203-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
