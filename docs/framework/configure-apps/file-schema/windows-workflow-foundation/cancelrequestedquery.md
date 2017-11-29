---
title: '&lt;cancelRequestedQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e1697b245f9ab61cab3e4b26b1756259f0eba9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcancelrequestedquerygt"></a><span data-ttu-id="7f81e-102">&lt;cancelRequestedQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="7f81e-102">&lt;cancelRequestedQuery&gt;</span></span>
<span data-ttu-id="7f81e-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f81e-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f81e-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7f81e-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7f81e-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="7f81e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="7f81e-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="7f81e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="7f81e-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="7f81e-107">\<tracking></span></span>  
<span data-ttu-id="7f81e-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="7f81e-108">\<trackingProfile></span></span>  
<span data-ttu-id="7f81e-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="7f81e-109">\<workflow></span></span>  
<span data-ttu-id="7f81e-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="7f81e-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="7f81e-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="7f81e-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f81e-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f81e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f81e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7f81e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7f81e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f81e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f81e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7f81e-115">Attributes</span></span>  
  
|<span data-ttu-id="7f81e-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7f81e-116">Attribute</span></span>|<span data-ttu-id="7f81e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="7f81e-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f81e-118">activityName</span><span class="sxs-lookup"><span data-stu-id="7f81e-118">activityName</span></span>|<span data-ttu-id="7f81e-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="7f81e-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="7f81e-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="7f81e-120">childActivityName</span></span>|<span data-ttu-id="7f81e-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="7f81e-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f81e-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7f81e-122">Child Elements</span></span>  
 <span data-ttu-id="7f81e-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="7f81e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f81e-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7f81e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7f81e-125">Element</span><span class="sxs-lookup"><span data-stu-id="7f81e-125">Element</span></span>|<span data-ttu-id="7f81e-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7f81e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f81e-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="7f81e-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="7f81e-128">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f81e-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7f81e-129">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7f81e-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f81e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f81e-130">See Also</span></span>  
 <span data-ttu-id="7f81e-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f81e-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="7f81e-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7f81e-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="7f81e-133">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="7f81e-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="7f81e-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7f81e-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
