---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398868"
---
# <a name="bookmarkresumptionqueries"></a><span data-ttu-id="7dbaa-101">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7dbaa-101">\<bookmarkResumptionQueries></span></span>
<span data-ttu-id="7dbaa-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-102">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7dbaa-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7dbaa-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7dbaa-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7dbaa-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7dbaa-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7dbaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7dbaa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7dbaa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7dbaa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="7dbaa-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="7dbaa-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7dbaa-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7dbaa-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7dbaa-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7dbaa-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7dbaa-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7dbaa-114">Attributes</span></span>  
 <span data-ttu-id="7dbaa-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7dbaa-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7dbaa-116">Child Elements</span></span>  
  
|<span data-ttu-id="7dbaa-117">Element</span><span class="sxs-lookup"><span data-stu-id="7dbaa-117">Element</span></span>|<span data-ttu-id="7dbaa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7dbaa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dbaa-119">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7dbaa-119">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery.md)|<span data-ttu-id="7dbaa-120">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-120">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7dbaa-121">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7dbaa-121">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7dbaa-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7dbaa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7dbaa-123">Element</span><span class="sxs-lookup"><span data-stu-id="7dbaa-123">Element</span></span>|<span data-ttu-id="7dbaa-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7dbaa-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7dbaa-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7dbaa-125">\<workflow></span></span>](workflow.md)|<span data-ttu-id="7dbaa-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="7dbaa-126">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7dbaa-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dbaa-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7dbaa-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7dbaa-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7dbaa-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7dbaa-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
