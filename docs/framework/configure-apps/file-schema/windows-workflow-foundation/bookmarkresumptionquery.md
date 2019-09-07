---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398848"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="a651c-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="a651c-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="a651c-102">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a651c-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="a651c-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="a651c-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="a651c-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="a651c-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a651c-106">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a651c-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="a651c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="a651c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="a651c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries.md)</span><span class="sxs-lookup"><span data-stu-id="a651c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)</span></span>\
<span data-ttu-id="a651c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="a651c-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a651c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="a651c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a651c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a651c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a651c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a651c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a651c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a651c-115">Attributes</span></span>  
  
|<span data-ttu-id="a651c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a651c-116">Attribute</span></span>|<span data-ttu-id="a651c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a651c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a651c-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="a651c-118">name</span></span>|<span data-ttu-id="a651c-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="a651c-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a651c-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a651c-120">Child Elements</span></span>  
 <span data-ttu-id="a651c-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="a651c-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a651c-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a651c-122">Parent Elements</span></span>  
  
|<span data-ttu-id="a651c-123">Element</span><span class="sxs-lookup"><span data-stu-id="a651c-123">Element</span></span>|<span data-ttu-id="a651c-124">Opis</span><span class="sxs-lookup"><span data-stu-id="a651c-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a651c-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="a651c-125">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="a651c-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a651c-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a651c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a651c-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a651c-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a651c-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a651c-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a651c-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
