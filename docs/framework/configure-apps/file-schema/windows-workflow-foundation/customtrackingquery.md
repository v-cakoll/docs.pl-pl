---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: 695fccf88ac0d8a672e710ccc632ea58dd2fc693
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398768"
---
# <a name="customtrackingquery"></a><span data-ttu-id="750f7-101">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="750f7-101">\<customTrackingQuery></span></span>
<span data-ttu-id="750f7-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="750f7-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="750f7-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="750f7-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="750f7-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="750f7-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="750f7-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="750f7-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="750f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="750f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="750f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="750f7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="750f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="750f7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750f7-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="750f7-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="750f7-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="750f7-113">Attributes and Elements</span></span>  
 <span data-ttu-id="750f7-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="750f7-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="750f7-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="750f7-115">Attributes</span></span>  
  
|<span data-ttu-id="750f7-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="750f7-116">Attribute</span></span>|<span data-ttu-id="750f7-117">Opis</span><span class="sxs-lookup"><span data-stu-id="750f7-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="750f7-118">activityName</span><span class="sxs-lookup"><span data-stu-id="750f7-118">activityName</span></span>|<span data-ttu-id="750f7-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="750f7-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="750f7-120">nazwa</span><span class="sxs-lookup"><span data-stu-id="750f7-120">name</span></span>|<span data-ttu-id="750f7-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="750f7-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="750f7-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="750f7-122">Child Elements</span></span>  
 <span data-ttu-id="750f7-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="750f7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="750f7-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="750f7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="750f7-125">Element</span><span class="sxs-lookup"><span data-stu-id="750f7-125">Element</span></span>|<span data-ttu-id="750f7-126">Opis</span><span class="sxs-lookup"><span data-stu-id="750f7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="750f7-127">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="750f7-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="750f7-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="750f7-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="750f7-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="750f7-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="750f7-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="750f7-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="750f7-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="750f7-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
