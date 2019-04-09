---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: e43ba66e2c3ccfbb723b1eea8ef6774ad3f9f2aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140039"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="61e51-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="61e51-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="61e51-102">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61e51-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="61e51-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="61e51-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="61e51-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="61e51-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="61e51-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="61e51-105">\<system.serviceModel></span></span>  
<span data-ttu-id="61e51-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="61e51-106">\<tracking></span></span>  
<span data-ttu-id="61e51-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="61e51-107">\<trackingProfile></span></span>  
<span data-ttu-id="61e51-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="61e51-108">\<workflow></span></span>  
<span data-ttu-id="61e51-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="61e51-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="61e51-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="61e51-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e51-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="61e51-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61e51-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61e51-112">Attributes and Elements</span></span>  
 <span data-ttu-id="61e51-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61e51-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61e51-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61e51-114">Attributes</span></span>  
  
|<span data-ttu-id="61e51-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61e51-115">Attribute</span></span>|<span data-ttu-id="61e51-116">Opis</span><span class="sxs-lookup"><span data-stu-id="61e51-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61e51-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="61e51-117">name</span></span>|<span data-ttu-id="61e51-118">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="61e51-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61e51-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61e51-119">Child Elements</span></span>  
 <span data-ttu-id="61e51-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="61e51-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="61e51-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61e51-121">Parent Elements</span></span>  
  
|<span data-ttu-id="61e51-122">Element</span><span class="sxs-lookup"><span data-stu-id="61e51-122">Element</span></span>|<span data-ttu-id="61e51-123">Opis</span><span class="sxs-lookup"><span data-stu-id="61e51-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61e51-124">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="61e51-124">\<bookmarkResumptionQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bookmarkresumptionqueries.md)|<span data-ttu-id="61e51-125">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="61e51-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="61e51-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61e51-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="61e51-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="61e51-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="61e51-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="61e51-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
