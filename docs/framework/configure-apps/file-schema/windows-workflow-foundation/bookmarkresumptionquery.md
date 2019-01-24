---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: a5eb00d1e094484e3ec01e0db18719ec50e4b953
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515075"
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="7f3ae-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="7f3ae-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="7f3ae-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="7f3ae-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="7f3ae-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7f3ae-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7f3ae-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7f3ae-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7f3ae-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7f3ae-107">\<tracking></span></span>  
<span data-ttu-id="7f3ae-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7f3ae-108">\<trackingProfile></span></span>  
<span data-ttu-id="7f3ae-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7f3ae-109">\<workflow></span></span>  
<span data-ttu-id="7f3ae-110">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7f3ae-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="7f3ae-111">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="7f3ae-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f3ae-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f3ae-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f3ae-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f3ae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7f3ae-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f3ae-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f3ae-115">Attributes</span></span>  
  
|<span data-ttu-id="7f3ae-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f3ae-116">Attribute</span></span>|<span data-ttu-id="7f3ae-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7f3ae-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f3ae-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="7f3ae-118">name</span></span>|<span data-ttu-id="7f3ae-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f3ae-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f3ae-120">Child Elements</span></span>  
 <span data-ttu-id="7f3ae-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f3ae-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f3ae-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7f3ae-123">Element</span><span class="sxs-lookup"><span data-stu-id="7f3ae-123">Element</span></span>|<span data-ttu-id="7f3ae-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7f3ae-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f3ae-125">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="7f3ae-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="7f3ae-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7f3ae-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f3ae-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f3ae-127">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="7f3ae-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7f3ae-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7f3ae-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7f3ae-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
