---
title: '&lt;cancelRequestedQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2af49aab76e82a97aeee92b4799b91011f70c509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="23bb4-102">&lt;cancelRequestedQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="23bb4-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="23bb4-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23bb4-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="23bb4-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="23bb4-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="23bb4-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="23bb4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="23bb4-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="23bb4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="23bb4-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="23bb4-107">\<tracking></span></span>  
<span data-ttu-id="23bb4-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="23bb4-108">\<trackingProfile></span></span>  
<span data-ttu-id="23bb4-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="23bb4-109">\<workflow></span></span>  
<span data-ttu-id="23bb4-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="23bb4-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="23bb4-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="23bb4-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23bb4-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="23bb4-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="23bb4-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23bb4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="23bb4-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23bb4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23bb4-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23bb4-115">Attributes</span></span>  
  
|<span data-ttu-id="23bb4-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23bb4-116">Attribute</span></span>|<span data-ttu-id="23bb4-117">Opis</span><span class="sxs-lookup"><span data-stu-id="23bb4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23bb4-118">activityName</span><span class="sxs-lookup"><span data-stu-id="23bb4-118">activityName</span></span>|<span data-ttu-id="23bb4-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="23bb4-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="23bb4-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="23bb4-120">childActivityName</span></span>|<span data-ttu-id="23bb4-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="23bb4-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23bb4-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23bb4-122">Child Elements</span></span>  
 <span data-ttu-id="23bb4-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="23bb4-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23bb4-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23bb4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="23bb4-125">Element</span><span class="sxs-lookup"><span data-stu-id="23bb4-125">Element</span></span>|<span data-ttu-id="23bb4-126">Opis</span><span class="sxs-lookup"><span data-stu-id="23bb4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23bb4-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="23bb4-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="23bb4-128">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23bb4-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="23bb4-129">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="23bb4-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23bb4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23bb4-130">See Also</span></span>  
 <span data-ttu-id="23bb4-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="23bb4-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="23bb4-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="23bb4-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="23bb4-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="23bb4-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="23bb4-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="23bb4-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
