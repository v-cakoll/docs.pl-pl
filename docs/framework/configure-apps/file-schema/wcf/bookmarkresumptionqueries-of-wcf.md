---
title: <bookmarkResumptionQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850128"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="27a99-102">\<bookmarkResumptionQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="27a99-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="27a99-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27a99-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="27a99-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="27a99-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="27a99-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="27a99-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="27a99-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="27a99-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="27a99-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="27a99-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="27a99-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27a99-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="27a99-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="27a99-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="27a99-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27a99-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="27a99-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="27a99-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="27a99-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bookmarkResumptionQueries >**</span><span class="sxs-lookup"><span data-stu-id="27a99-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="27a99-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="27a99-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="27a99-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="27a99-114">Attributes and elements</span></span>  
  
<span data-ttu-id="27a99-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="27a99-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="27a99-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="27a99-116">Attributes</span></span>  
  
<span data-ttu-id="27a99-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="27a99-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="27a99-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="27a99-118">Child elements</span></span>  
  
|<span data-ttu-id="27a99-119">Element</span><span class="sxs-lookup"><span data-stu-id="27a99-119">Element</span></span>|<span data-ttu-id="27a99-120">Opis</span><span class="sxs-lookup"><span data-stu-id="27a99-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27a99-121">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="27a99-121">\<bookmarkResumptionQuery></span></span>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="27a99-122">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27a99-122">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="27a99-123">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="27a99-123">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="27a99-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="27a99-124">Parent elements</span></span>  
  
|<span data-ttu-id="27a99-125">Element</span><span class="sxs-lookup"><span data-stu-id="27a99-125">Element</span></span>|<span data-ttu-id="27a99-126">Opis</span><span class="sxs-lookup"><span data-stu-id="27a99-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="27a99-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="27a99-127">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="27a99-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="27a99-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27a99-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27a99-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="27a99-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="27a99-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="27a99-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="27a99-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
