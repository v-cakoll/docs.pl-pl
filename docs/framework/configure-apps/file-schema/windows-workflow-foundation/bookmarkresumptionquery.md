---
title: '&lt;bookmarkResumptionQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 88f9639e4ecc3105a0e58d92e443d9582f261970
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756189"
---
# <a name="ltbookmarkresumptionquerygt"></a><span data-ttu-id="cdece-102">&lt;bookmarkResumptionQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="cdece-102">&lt;bookmarkResumptionQuery&gt;</span></span>
<span data-ttu-id="cdece-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cdece-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="cdece-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="cdece-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="cdece-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="cdece-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="cdece-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cdece-106">\<system.serviceModel></span></span>  
<span data-ttu-id="cdece-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="cdece-107">\<tracking></span></span>  
<span data-ttu-id="cdece-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="cdece-108">\<trackingProfile></span></span>  
<span data-ttu-id="cdece-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="cdece-109">\<workflow></span></span>  
<span data-ttu-id="cdece-110">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="cdece-110">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="cdece-111">\<bookmarkResumptionQuery ></span><span class="sxs-lookup"><span data-stu-id="cdece-111">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdece-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdece-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdece-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cdece-113">Attributes and Elements</span></span>  
 <span data-ttu-id="cdece-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cdece-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdece-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cdece-115">Attributes</span></span>  
  
|<span data-ttu-id="cdece-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cdece-116">Attribute</span></span>|<span data-ttu-id="cdece-117">Opis</span><span class="sxs-lookup"><span data-stu-id="cdece-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdece-118">nazwa</span><span class="sxs-lookup"><span data-stu-id="cdece-118">name</span></span>|<span data-ttu-id="cdece-119">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="cdece-119">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdece-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cdece-120">Child Elements</span></span>  
 <span data-ttu-id="cdece-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="cdece-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdece-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cdece-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cdece-123">Element</span><span class="sxs-lookup"><span data-stu-id="cdece-123">Element</span></span>|<span data-ttu-id="cdece-124">Opis</span><span class="sxs-lookup"><span data-stu-id="cdece-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdece-125">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="cdece-125">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="cdece-126">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="cdece-126">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdece-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdece-127">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="cdece-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="cdece-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="cdece-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="cdece-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
