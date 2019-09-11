---
title: <customTrackingQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 2c4bd74ae346c536e8bc0ae454e638b7c76a40fc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855431"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="059e5-102">\<customTrackingQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="059e5-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="059e5-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="059e5-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="059e5-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="059e5-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
<span data-ttu-id="059e5-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="059e5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="059e5-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="059e5-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="059e5-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="059e5-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="059e5-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="059e5-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="059e5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="059e5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="059e5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="059e5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="059e5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="059e5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="059e5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<customTrackingQueries >**</span><span class="sxs-lookup"><span data-stu-id="059e5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<customTrackingQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="059e5-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="059e5-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="059e5-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="059e5-114">Attributes and elements</span></span>

<span data-ttu-id="059e5-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="059e5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="059e5-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="059e5-116">Attributes</span></span>

<span data-ttu-id="059e5-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="059e5-117">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="059e5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="059e5-118">Child elements</span></span>
  
|<span data-ttu-id="059e5-119">Element</span><span class="sxs-lookup"><span data-stu-id="059e5-119">Element</span></span>|<span data-ttu-id="059e5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="059e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="059e5-121">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="059e5-121">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="059e5-122">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="059e5-122">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="059e5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="059e5-123">Parent elements</span></span>  
  
|<span data-ttu-id="059e5-124">Element</span><span class="sxs-lookup"><span data-stu-id="059e5-124">Element</span></span>|<span data-ttu-id="059e5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="059e5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="059e5-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="059e5-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="059e5-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="059e5-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="059e5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="059e5-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="059e5-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="059e5-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="059e5-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="059e5-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
