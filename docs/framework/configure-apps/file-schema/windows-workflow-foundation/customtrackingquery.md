---
title: <customTrackingQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e108e89-1132-46b7-868a-c7f5c69dc89f
ms.openlocfilehash: a02d71811709b2c285ab7081b89ee3082ec5b43d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152212"
---
# <a name="customtrackingquery"></a><span data-ttu-id="0f74a-101">\<> customTrackingQuery</span><span class="sxs-lookup"><span data-stu-id="0f74a-101">\<customTrackingQuery></span></span>
<span data-ttu-id="0f74a-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="0f74a-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0f74a-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="0f74a-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0f74a-104">Aby uzyskać więcej informacji na temat śledzenia zapytań profilowych, zobacz [Śledzenie profili](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0f74a-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0f74a-106">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0f74a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0f74a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0f74a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0f74a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span><span class="sxs-lookup"><span data-stu-id="0f74a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries.md)</span></span>\
<span data-ttu-id="0f74a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>customTrackingQuery**</span><span class="sxs-lookup"><span data-stu-id="0f74a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f74a-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f74a-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f74a-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f74a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="0f74a-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f74a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f74a-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f74a-115">Attributes</span></span>  
  
|<span data-ttu-id="0f74a-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0f74a-116">Attribute</span></span>|<span data-ttu-id="0f74a-117">Opis</span><span class="sxs-lookup"><span data-stu-id="0f74a-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f74a-118">activityName</span><span class="sxs-lookup"><span data-stu-id="0f74a-118">activityName</span></span>|<span data-ttu-id="0f74a-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="0f74a-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|<span data-ttu-id="0f74a-120">name</span><span class="sxs-lookup"><span data-stu-id="0f74a-120">name</span></span>|<span data-ttu-id="0f74a-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="0f74a-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f74a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f74a-122">Child Elements</span></span>  
 <span data-ttu-id="0f74a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="0f74a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f74a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f74a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0f74a-125">Element</span><span class="sxs-lookup"><span data-stu-id="0f74a-125">Element</span></span>|<span data-ttu-id="0f74a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0f74a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f74a-127">\<>customTrackingQuery</span><span class="sxs-lookup"><span data-stu-id="0f74a-127">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="0f74a-128">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="0f74a-128">A query that is used to track events that you define in your code activities.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f74a-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f74a-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0f74a-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0f74a-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0f74a-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="0f74a-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
