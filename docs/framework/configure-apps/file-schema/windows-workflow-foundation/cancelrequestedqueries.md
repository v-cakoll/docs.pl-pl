---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 5bc2e3ffeb93bdfcd45638d6b50e218c03706f42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520688"
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="7bf45-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="7bf45-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="7bf45-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7bf45-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7bf45-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7bf45-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7bf45-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7bf45-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7bf45-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7bf45-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7bf45-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7bf45-107">\<tracking></span></span>  
<span data-ttu-id="7bf45-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="7bf45-108">\<trackingProfile></span></span>  
<span data-ttu-id="7bf45-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7bf45-109">\<workflow></span></span>  
<span data-ttu-id="7bf45-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="7bf45-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf45-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bf45-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bf45-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7bf45-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7bf45-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7bf45-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bf45-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7bf45-114">Attributes</span></span>  
 <span data-ttu-id="7bf45-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="7bf45-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7bf45-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7bf45-116">Child Elements</span></span>  
  
|<span data-ttu-id="7bf45-117">Element</span><span class="sxs-lookup"><span data-stu-id="7bf45-117">Element</span></span>|<span data-ttu-id="7bf45-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7bf45-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf45-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="7bf45-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="7bf45-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7bf45-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7bf45-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7bf45-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7bf45-122">Element</span><span class="sxs-lookup"><span data-stu-id="7bf45-122">Element</span></span>|<span data-ttu-id="7bf45-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7bf45-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bf45-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7bf45-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="7bf45-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7bf45-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bf45-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bf45-126">See also</span></span>
- [<span data-ttu-id="7bf45-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7bf45-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7bf45-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7bf45-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
