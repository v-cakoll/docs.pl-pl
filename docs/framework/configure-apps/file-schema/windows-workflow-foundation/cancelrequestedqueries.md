---
title: '&lt;cancelRequestedQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 457cc3aaa921016e553eb40bcee72af5de3c7179
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcancelrequestedqueriesgt"></a><span data-ttu-id="6bf8c-102">&lt;cancelRequestedQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="6bf8c-102">&lt;cancelRequestedQueries&gt;</span></span>
<span data-ttu-id="6bf8c-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-103">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6bf8c-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="6bf8c-105">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="6bf8c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="6bf8c-106">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="6bf8c-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-107">\<tracking></span></span>  
<span data-ttu-id="6bf8c-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-108">\<trackingProfile></span></span>  
<span data-ttu-id="6bf8c-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-109">\<workflow></span></span>  
<span data-ttu-id="6bf8c-110">\<cancelRequestedQueries ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-110">\<cancelRequestedQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf8c-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bf8c-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6bf8c-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6bf8c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6bf8c-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6bf8c-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6bf8c-114">Attributes</span></span>  
 <span data-ttu-id="6bf8c-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6bf8c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6bf8c-116">Child Elements</span></span>  
  
|<span data-ttu-id="6bf8c-117">Element</span><span class="sxs-lookup"><span data-stu-id="6bf8c-117">Element</span></span>|<span data-ttu-id="6bf8c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="6bf8c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bf8c-119">\<cancelRequestedQuery ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-119">\<cancelRequestedQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|<span data-ttu-id="6bf8c-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6bf8c-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6bf8c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6bf8c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6bf8c-122">Element</span><span class="sxs-lookup"><span data-stu-id="6bf8c-122">Element</span></span>|<span data-ttu-id="6bf8c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6bf8c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6bf8c-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="6bf8c-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="6bf8c-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6bf8c-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bf8c-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bf8c-126">See Also</span></span>  
 [<span data-ttu-id="6bf8c-127">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="6bf8c-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="6bf8c-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="6bf8c-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
