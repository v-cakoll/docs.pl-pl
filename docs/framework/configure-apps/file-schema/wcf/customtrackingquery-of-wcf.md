---
title: <customTrackingQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: 204bbb6cf5ebcb30bf92b697885ecbbbd94385e0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855420"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="4890c-102">\<customTrackingQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="4890c-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="4890c-103">Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4890c-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="4890c-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="4890c-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="4890c-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4890c-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4890c-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4890c-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="4890c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="4890c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="4890c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="4890c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="4890c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customTrackingQueries >** ](customtrackingqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="4890c-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customTrackingQueries>**](customtrackingqueries-of-wcf.md)</span></span>\
<span data-ttu-id="4890c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQuery >**</span><span class="sxs-lookup"><span data-stu-id="4890c-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4890c-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="4890c-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4890c-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4890c-115">Attributes and elements</span></span>  

<span data-ttu-id="4890c-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4890c-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4890c-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4890c-117">Attributes</span></span>  
  
|<span data-ttu-id="4890c-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4890c-118">Attribute</span></span>|<span data-ttu-id="4890c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4890c-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="4890c-120">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4890c-120">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="4890c-121">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="4890c-121">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4890c-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4890c-122">Child elements</span></span>

<span data-ttu-id="4890c-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="4890c-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4890c-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4890c-124">Parent elements</span></span>

|<span data-ttu-id="4890c-125">Element</span><span class="sxs-lookup"><span data-stu-id="4890c-125">Element</span></span>|<span data-ttu-id="4890c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4890c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4890c-127">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="4890c-127">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="4890c-128">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="4890c-128">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="4890c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4890c-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4890c-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4890c-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4890c-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4890c-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
