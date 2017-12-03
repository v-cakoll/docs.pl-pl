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
ms.openlocfilehash: 6fc9df52c691e13802607714977f3aa778cde84e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedquerygt-of-wcf"></a><span data-ttu-id="4d883-102">&lt;cancelRequestedQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="4d883-102">&lt;cancelRequestedQuery&gt; of WCF</span></span>
<span data-ttu-id="4d883-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d883-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4d883-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d883-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="4d883-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4d883-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="4d883-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4d883-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4d883-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="4d883-107">\<tracking></span></span>  
<span data-ttu-id="4d883-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4d883-108">\<trackingProfile></span></span>  
<span data-ttu-id="4d883-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4d883-109">\<workflow></span></span>  
<span data-ttu-id="4d883-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="4d883-110">\<cancelRequestedQueries></span></span>  
<span data-ttu-id="4d883-111">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="4d883-111">\<cancelRequestedQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d883-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d883-112">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d883-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d883-113">Attributes and Elements</span></span>  
 <span data-ttu-id="4d883-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d883-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d883-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d883-115">Attributes</span></span>  
  
|<span data-ttu-id="4d883-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4d883-116">Attribute</span></span>|<span data-ttu-id="4d883-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4d883-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d883-118">activityName</span><span class="sxs-lookup"><span data-stu-id="4d883-118">activityName</span></span>|<span data-ttu-id="4d883-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="4d883-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="4d883-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="4d883-120">childActivityName</span></span>|<span data-ttu-id="4d883-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="4d883-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d883-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d883-122">Child Elements</span></span>  
 <span data-ttu-id="4d883-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d883-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d883-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d883-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4d883-125">Element</span><span class="sxs-lookup"><span data-stu-id="4d883-125">Element</span></span>|<span data-ttu-id="4d883-126">Opis</span><span class="sxs-lookup"><span data-stu-id="4d883-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d883-127">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="4d883-127">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="4d883-128">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d883-128">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4d883-129">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d883-129">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d883-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d883-130">See Also</span></span>  
 <span data-ttu-id="4d883-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4d883-131"><xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="4d883-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="4d883-132"><xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType></span></span>     
 [<span data-ttu-id="4d883-133">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="4d883-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4d883-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4d883-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
