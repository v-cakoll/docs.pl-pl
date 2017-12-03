---
title: '&lt;activityStateQueries&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ec6cb2d077f95f53a2ee0daf8e2819ae91cb13b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="28028-102">&lt;activityStateQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="28028-102">&lt;activityStateQueries&gt; of WCF</span></span>
<span data-ttu-id="28028-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="28028-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="28028-104">Na przykład może być do śledzenia każdorazowo po ukończeniu działania "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="28028-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="28028-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="28028-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="28028-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="28028-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="28028-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="28028-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="28028-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="28028-108">\<system.serviceModel></span></span>  
<span data-ttu-id="28028-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="28028-109">\<tracking></span></span>  
<span data-ttu-id="28028-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="28028-110">\<trackingProfile></span></span>  
<span data-ttu-id="28028-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="28028-111">\<workflow></span></span>  
<span data-ttu-id="28028-112">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="28028-112">\<activityStateQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28028-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="28028-113">Syntax</span></span>  
  
```xml  
<tracking>   <trackingProfile name="Name">       <workflow>          <activityStateQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>       </workflow>   </trackingProfile></tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28028-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="28028-114">Attributes and Elements</span></span>  
 <span data-ttu-id="28028-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="28028-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28028-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="28028-116">Attributes</span></span>  
 <span data-ttu-id="28028-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="28028-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="28028-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="28028-118">Child Elements</span></span>  
  
|<span data-ttu-id="28028-119">Element</span><span class="sxs-lookup"><span data-stu-id="28028-119">Element</span></span>|<span data-ttu-id="28028-120">Opis</span><span class="sxs-lookup"><span data-stu-id="28028-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28028-121">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="28028-121">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="28028-122">Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="28028-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="28028-123">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="28028-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28028-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="28028-124">Parent Elements</span></span>  
  
|<span data-ttu-id="28028-125">Element</span><span class="sxs-lookup"><span data-stu-id="28028-125">Element</span></span>|<span data-ttu-id="28028-126">Opis</span><span class="sxs-lookup"><span data-stu-id="28028-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28028-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="28028-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="28028-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="28028-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28028-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28028-129">See Also</span></span>  
 <span data-ttu-id="28028-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span><span class="sxs-lookup"><span data-stu-id="28028-130"><xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection></span></span>    
 <span data-ttu-id="28028-131"><xref:System.Activities.Tracking.ActivityStateQuery></span><span class="sxs-lookup"><span data-stu-id="28028-131"><xref:System.Activities.Tracking.ActivityStateQuery></span></span>    
 [<span data-ttu-id="28028-132">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="28028-132">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="28028-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="28028-133">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
