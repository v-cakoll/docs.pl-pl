---
title: '&lt;faultPropagationQueries&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 25390635f54fb24598b63d220eaf6bddea46eead
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="1a3e5-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="1a3e5-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="1a3e5-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1a3e5-104">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="1a3e5-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="1a3e5-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="1a3e5-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="1a3e5-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="1a3e5-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-108">\<system.serviceModel></span></span>  
<span data-ttu-id="1a3e5-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-109">\<tracking></span></span>  
<span data-ttu-id="1a3e5-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-110">\<trackingProfile></span></span>  
<span data-ttu-id="1a3e5-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-111">\<workflow></span></span>  
<span data-ttu-id="1a3e5-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a3e5-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a3e5-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String" 
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a3e5-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1a3e5-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1a3e5-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a3e5-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1a3e5-116">Attributes</span></span>  
 <span data-ttu-id="1a3e5-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1a3e5-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1a3e5-118">Child Elements</span></span>  
  
|<span data-ttu-id="1a3e5-119">Element</span><span class="sxs-lookup"><span data-stu-id="1a3e5-119">Element</span></span>|<span data-ttu-id="1a3e5-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1a3e5-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a3e5-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="1a3e5-122">Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="1a3e5-123">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1a3e5-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1a3e5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1a3e5-125">Element</span><span class="sxs-lookup"><span data-stu-id="1a3e5-125">Element</span></span>|<span data-ttu-id="1a3e5-126">Opis</span><span class="sxs-lookup"><span data-stu-id="1a3e5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a3e5-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="1a3e5-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="1a3e5-128">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1a3e5-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a3e5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a3e5-129">See Also</span></span>  
 <span data-ttu-id="1a3e5-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1a3e5-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="1a3e5-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="1a3e5-131"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="1a3e5-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="1a3e5-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="1a3e5-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="1a3e5-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
