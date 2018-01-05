---
title: '&lt;cancelRequestedQueries&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f31663d44774f84feab76f22f19400a955a3cf8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a><span data-ttu-id="4d0a2-102">&lt;cancelRequestedQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="4d0a2-102">&lt;cancelRequestedQueries&gt; of WCF</span></span>
<span data-ttu-id="4d0a2-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d0a2-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4d0a2-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="4d0a2-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="4d0a2-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4d0a2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
 <span data-ttu-id="4d0a2-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4d0a2-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-107">\<tracking></span></span>  
<span data-ttu-id="4d0a2-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-108">\<trackingProfile></span></span>  
<span data-ttu-id="4d0a2-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-109">\<workflow></span></span>  
<span data-ttu-id="4d0a2-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d0a2-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d0a2-111">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4d0a2-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d0a2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4d0a2-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d0a2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d0a2-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d0a2-114">Attributes</span></span>  
 <span data-ttu-id="4d0a2-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d0a2-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d0a2-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d0a2-116">Child Elements</span></span>  
  
|<span data-ttu-id="4d0a2-117">Element</span><span class="sxs-lookup"><span data-stu-id="4d0a2-117">Element</span></span>|<span data-ttu-id="4d0a2-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4d0a2-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d0a2-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="4d0a2-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d0a2-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d0a2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d0a2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4d0a2-122">Element</span><span class="sxs-lookup"><span data-stu-id="4d0a2-122">Element</span></span>|<span data-ttu-id="4d0a2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4d0a2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d0a2-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="4d0a2-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="4d0a2-125">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4d0a2-125">A configuration element that contains all queries for a specific workflow identified by the `a HYPERLINK "http://msdn.microsoft.com/en-us/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d0a2-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d0a2-126">See Also</span></span>  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [<span data-ttu-id="4d0a2-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4d0a2-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="4d0a2-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4d0a2-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
