---
title: '&lt;faultPropagationQuery&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 650be6a52651f9f55a868d135fd7d0dfa84b967a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="23752-102">&lt;faultPropagationQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="23752-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="23752-103">Reprezentuje zapytanie, które jest używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="23752-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="23752-104">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="23752-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="23752-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="23752-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="23752-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="23752-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="23752-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="23752-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="23752-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="23752-108">\<system.serviceModel></span></span>  
<span data-ttu-id="23752-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="23752-109">\<tracking></span></span>  
<span data-ttu-id="23752-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="23752-110">\<trackingProfile></span></span>  
<span data-ttu-id="23752-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="23752-111">\<workflow></span></span>  
<span data-ttu-id="23752-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="23752-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="23752-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="23752-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23752-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="23752-114">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23752-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="23752-115">Attributes and Elements</span></span>  
 <span data-ttu-id="23752-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="23752-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23752-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="23752-117">Attributes</span></span>  
  
|<span data-ttu-id="23752-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="23752-118">Attribute</span></span>|<span data-ttu-id="23752-119">Opis</span><span class="sxs-lookup"><span data-stu-id="23752-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="23752-120">activityName</span><span class="sxs-lookup"><span data-stu-id="23752-120">activityName</span></span>|<span data-ttu-id="23752-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="23752-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="23752-122">Wartość domyślna to *, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="23752-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="23752-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="23752-123">faultHandlerActivityName</span></span>|<span data-ttu-id="23752-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="23752-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="23752-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="23752-125">Child Elements</span></span>  
 <span data-ttu-id="23752-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="23752-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="23752-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="23752-127">Parent Elements</span></span>  
  
|<span data-ttu-id="23752-128">Element</span><span class="sxs-lookup"><span data-stu-id="23752-128">Element</span></span>|<span data-ttu-id="23752-129">Opis</span><span class="sxs-lookup"><span data-stu-id="23752-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23752-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="23752-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="23752-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="23752-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="23752-132">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="23752-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23752-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23752-133">See Also</span></span>  
 <span data-ttu-id="23752-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="23752-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="23752-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="23752-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="23752-136">Przepływ pracy, kontrola i śledzenie</span><span class="sxs-lookup"><span data-stu-id="23752-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="23752-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="23752-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
