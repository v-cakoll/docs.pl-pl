---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: 9043deb66e1a4314df97f4da41103e74676a270c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945959"
---
# <a name="bookmarkresumptionquery"></a><span data-ttu-id="f6064-101">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f6064-101">\<bookmarkResumptionQuery></span></span>
<span data-ttu-id="f6064-102">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f6064-102">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="f6064-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="f6064-103">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="f6064-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="f6064-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="f6064-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f6064-105">\<system.serviceModel></span></span>  
<span data-ttu-id="f6064-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f6064-106">\<tracking></span></span>  
<span data-ttu-id="f6064-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f6064-107">\<trackingProfile></span></span>  
<span data-ttu-id="f6064-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f6064-108">\<workflow></span></span>  
<span data-ttu-id="f6064-109">\<bookmarkResumptionQueries></span><span class="sxs-lookup"><span data-stu-id="f6064-109">\<bookmarkResumptionQueries></span></span>  
<span data-ttu-id="f6064-110">\<bookmarkResumptionQuery></span><span class="sxs-lookup"><span data-stu-id="f6064-110">\<bookmarkResumptionQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6064-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6064-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6064-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6064-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f6064-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6064-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6064-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6064-114">Attributes</span></span>  
  
|<span data-ttu-id="f6064-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6064-115">Attribute</span></span>|<span data-ttu-id="f6064-116">Opis</span><span class="sxs-lookup"><span data-stu-id="f6064-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6064-117">nazwa</span><span class="sxs-lookup"><span data-stu-id="f6064-117">name</span></span>|<span data-ttu-id="f6064-118">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="f6064-118">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6064-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6064-119">Child Elements</span></span>  
 <span data-ttu-id="f6064-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="f6064-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6064-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6064-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f6064-122">Element</span><span class="sxs-lookup"><span data-stu-id="f6064-122">Element</span></span>|<span data-ttu-id="f6064-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f6064-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6064-124">\<bookmarkResumptionQueries ></span><span class="sxs-lookup"><span data-stu-id="f6064-124">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="f6064-125">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f6064-125">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6064-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6064-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f6064-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f6064-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f6064-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f6064-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
