---
title: '&lt;cancelRequestedQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e532ea482108c9a5cabe13a99afddca10f8341d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767040"
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="755a5-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="755a5-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="755a5-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="755a5-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="755a5-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="755a5-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="755a5-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="755a5-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="755a5-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="755a5-106">\<system.serviceModel></span></span>  
<span data-ttu-id="755a5-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="755a5-107">\<tracking></span></span>  
<span data-ttu-id="755a5-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="755a5-108">\<trackingProfile></span></span>  
<span data-ttu-id="755a5-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="755a5-109">\<workflow></span></span>  
<span data-ttu-id="755a5-110">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="755a5-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="755a5-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="755a5-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="755a5-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="755a5-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="755a5-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="755a5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="755a5-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="755a5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="755a5-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="755a5-115">Attributes</span></span>  
  
|<span data-ttu-id="755a5-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="755a5-116">Attribute</span></span>|<span data-ttu-id="755a5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="755a5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="755a5-118">activityName</span><span class="sxs-lookup"><span data-stu-id="755a5-118">activityName</span></span>|<span data-ttu-id="755a5-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="755a5-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="755a5-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="755a5-120">childActivityName</span></span>|<span data-ttu-id="755a5-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="755a5-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="755a5-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="755a5-122">Child Elements</span></span>  
 <span data-ttu-id="755a5-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="755a5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="755a5-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="755a5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="755a5-125">Element</span><span class="sxs-lookup"><span data-stu-id="755a5-125">Element</span></span>|<span data-ttu-id="755a5-126">Opis</span><span class="sxs-lookup"><span data-stu-id="755a5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="755a5-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="755a5-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="755a5-128">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="755a5-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="755a5-129">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="755a5-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="755a5-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="755a5-130">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="755a5-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="755a5-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="755a5-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="755a5-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
