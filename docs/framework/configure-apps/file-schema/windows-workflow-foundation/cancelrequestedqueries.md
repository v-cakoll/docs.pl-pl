---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 32a37fb3cc2b93046bea133f351185638b0d7545
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163166"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="e7ca5-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="e7ca5-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="e7ca5-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="e7ca5-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="e7ca5-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e7ca5-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e7ca5-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e7ca5-105">\<system.serviceModel></span></span>  
<span data-ttu-id="e7ca5-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e7ca5-106">\<tracking></span></span>  
<span data-ttu-id="e7ca5-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e7ca5-107">\<trackingProfile></span></span>  
<span data-ttu-id="e7ca5-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e7ca5-108">\<workflow></span></span>  
<span data-ttu-id="e7ca5-109">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="e7ca5-109">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ca5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7ca5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ca5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7ca5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ca5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ca5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7ca5-113">Attributes</span></span>  
 <span data-ttu-id="e7ca5-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7ca5-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ca5-115">Child Elements</span></span>  
  
|<span data-ttu-id="e7ca5-116">Element</span><span class="sxs-lookup"><span data-stu-id="e7ca5-116">Element</span></span>|<span data-ttu-id="e7ca5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ca5-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ca5-118">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="e7ca5-118">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="e7ca5-119">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ca5-119">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ca5-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7ca5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ca5-121">Element</span><span class="sxs-lookup"><span data-stu-id="e7ca5-121">Element</span></span>|<span data-ttu-id="e7ca5-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e7ca5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ca5-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e7ca5-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e7ca5-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e7ca5-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7ca5-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7ca5-125">See also</span></span>

- [<span data-ttu-id="e7ca5-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e7ca5-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e7ca5-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e7ca5-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
