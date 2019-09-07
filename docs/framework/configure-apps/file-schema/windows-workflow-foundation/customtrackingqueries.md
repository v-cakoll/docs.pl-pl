---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 398b018ce407aee0687c95037753f3affa07aa9b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398781"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="0d7be-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="0d7be-101">\<customTrackingQueries></span></span>
<span data-ttu-id="0d7be-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="0d7be-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="0d7be-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="0d7be-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="0d7be-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="0d7be-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d7be-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="0d7be-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="0d7be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="0d7be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0d7be-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="0d7be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="0d7be-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7be-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d7be-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d7be-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0d7be-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0d7be-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0d7be-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d7be-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0d7be-114">Attributes</span></span>  
 <span data-ttu-id="0d7be-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="0d7be-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0d7be-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0d7be-116">Child Elements</span></span>  
  
|<span data-ttu-id="0d7be-117">Element</span><span class="sxs-lookup"><span data-stu-id="0d7be-117">Element</span></span>|<span data-ttu-id="0d7be-118">Opis</span><span class="sxs-lookup"><span data-stu-id="0d7be-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d7be-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="0d7be-119">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="0d7be-120">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="0d7be-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d7be-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0d7be-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0d7be-122">Element</span><span class="sxs-lookup"><span data-stu-id="0d7be-122">Element</span></span>|<span data-ttu-id="0d7be-123">Opis</span><span class="sxs-lookup"><span data-stu-id="0d7be-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d7be-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="0d7be-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="0d7be-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="0d7be-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d7be-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d7be-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="0d7be-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="0d7be-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="0d7be-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="0d7be-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
