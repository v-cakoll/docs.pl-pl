---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 628dbf801cae5f61dc7d518c27df3380dd2d3d23
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945948"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="38894-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="38894-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="38894-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38894-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="38894-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="38894-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="38894-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="38894-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="38894-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="38894-105">\<system.serviceModel></span></span>  
<span data-ttu-id="38894-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="38894-106">\<tracking></span></span>  
<span data-ttu-id="38894-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="38894-107">\<trackingProfile></span></span>  
<span data-ttu-id="38894-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="38894-108">\<workflow></span></span>  
<span data-ttu-id="38894-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="38894-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38894-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="38894-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String" 
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38894-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38894-111">Attributes and Elements</span></span>  
 <span data-ttu-id="38894-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38894-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38894-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38894-113">Attributes</span></span>  
 <span data-ttu-id="38894-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="38894-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="38894-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38894-115">Child Elements</span></span>  
  
|<span data-ttu-id="38894-116">Element</span><span class="sxs-lookup"><span data-stu-id="38894-116">Element</span></span>|<span data-ttu-id="38894-117">Opis</span><span class="sxs-lookup"><span data-stu-id="38894-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38894-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="38894-118">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="38894-119">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38894-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="38894-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38894-120">Parent Elements</span></span>  
  
|<span data-ttu-id="38894-121">Element</span><span class="sxs-lookup"><span data-stu-id="38894-121">Element</span></span>|<span data-ttu-id="38894-122">Opis</span><span class="sxs-lookup"><span data-stu-id="38894-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38894-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="38894-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="38894-124">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="38894-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38894-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38894-125">See also</span></span>

- [<span data-ttu-id="38894-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="38894-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="38894-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="38894-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
