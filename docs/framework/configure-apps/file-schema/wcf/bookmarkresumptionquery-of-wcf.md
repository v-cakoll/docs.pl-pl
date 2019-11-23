---
title: <bookmarkResumptionQuery> WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834002"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="03d2d-102">\<bookmarkResumptionQuery > z WCF</span><span class="sxs-lookup"><span data-stu-id="03d2d-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="03d2d-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03d2d-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="03d2d-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="03d2d-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="03d2d-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="03d2d-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="03d2d-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="03d2d-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="03d2d-107">&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="03d2d-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="03d2d-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<śledzenie**](tracking-of-wcf.md) ></span><span class="sxs-lookup"><span data-stu-id="03d2d-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="03d2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**Profile** ></span><span class="sxs-lookup"><span data-stu-id="03d2d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="03d2d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="03d2d-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="03d2d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływu**](workflow-of-wcf.md) ></span><span class="sxs-lookup"><span data-stu-id="03d2d-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="03d2d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bookmarkResumptionQueries >** ](bookmarkresumptionqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="03d2d-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)</span></span>\
<span data-ttu-id="03d2d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**bookmarkResumptionQuery >**</span><span class="sxs-lookup"><span data-stu-id="03d2d-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03d2d-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="03d2d-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03d2d-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="03d2d-115">Attributes and elements</span></span>

<span data-ttu-id="03d2d-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="03d2d-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03d2d-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="03d2d-117">Attributes</span></span>  
  
|<span data-ttu-id="03d2d-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="03d2d-118">Attribute</span></span>|<span data-ttu-id="03d2d-119">Opis</span><span class="sxs-lookup"><span data-stu-id="03d2d-119">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="03d2d-120">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="03d2d-120">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03d2d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="03d2d-121">Child elements</span></span>

<span data-ttu-id="03d2d-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="03d2d-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="03d2d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="03d2d-123">Parent elements</span></span>  
  
|<span data-ttu-id="03d2d-124">Element</span><span class="sxs-lookup"><span data-stu-id="03d2d-124">Element</span></span>|<span data-ttu-id="03d2d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="03d2d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="03d2d-126">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="03d2d-126">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="03d2d-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="03d2d-127">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="03d2d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03d2d-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="03d2d-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="03d2d-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="03d2d-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="03d2d-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
