---
title: '&lt;cancelRequestedQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 2abb2dc05bfec4419ca49d1517084ebc208e81e4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="23481-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="23481-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="23481-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23481-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="23481-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="23481-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="23481-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="23481-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="23481-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="23481-106">\<system.serviceModel></span></span>  
<span data-ttu-id="23481-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="23481-107">\<tracking></span></span>  
<span data-ttu-id="23481-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="23481-108">\<trackingProfile></span></span>  
<span data-ttu-id="23481-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="23481-109">\<workflow></span></span>  
<span data-ttu-id="23481-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="23481-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23481-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="23481-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23481-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23481-112">Attributes and Elements</span></span>  
 <span data-ttu-id="23481-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23481-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23481-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23481-114">Attributes</span></span>  
 <span data-ttu-id="23481-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="23481-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23481-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23481-116">Child Elements</span></span>  
  
|<span data-ttu-id="23481-117">Element</span><span class="sxs-lookup"><span data-stu-id="23481-117">Element</span></span>|<span data-ttu-id="23481-118">Opis</span><span class="sxs-lookup"><span data-stu-id="23481-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23481-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="23481-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="23481-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23481-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23481-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23481-121">Parent Elements</span></span>  
  
|<span data-ttu-id="23481-122">Element</span><span class="sxs-lookup"><span data-stu-id="23481-122">Element</span></span>|<span data-ttu-id="23481-123">Opis</span><span class="sxs-lookup"><span data-stu-id="23481-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23481-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="23481-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="23481-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="23481-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23481-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23481-126">See Also</span></span>  
 [<span data-ttu-id="23481-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="23481-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="23481-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="23481-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
