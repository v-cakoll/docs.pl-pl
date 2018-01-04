---
title: '&lt;faultPropagationQuery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244ae0db12964e2baf6de15f545cfa40152ee88e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="55f00-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="55f00-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="55f00-103">Reprezentuje zapytanie, które jest używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="55f00-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="55f00-104">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="55f00-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="55f00-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="55f00-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="55f00-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="55f00-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="55f00-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="55f00-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="55f00-108">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="55f00-108">\<system.serviceModel></span></span>  
<span data-ttu-id="55f00-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="55f00-109">\<tracking></span></span>  
<span data-ttu-id="55f00-110">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="55f00-110">\<trackingProfile></span></span>  
<span data-ttu-id="55f00-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="55f00-111">\<workflow></span></span>  
<span data-ttu-id="55f00-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="55f00-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="55f00-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="55f00-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f00-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="55f00-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55f00-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="55f00-115">Attributes and Elements</span></span>  
 <span data-ttu-id="55f00-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="55f00-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55f00-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="55f00-117">Attributes</span></span>  
  
|<span data-ttu-id="55f00-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="55f00-118">Attribute</span></span>|<span data-ttu-id="55f00-119">Opis</span><span class="sxs-lookup"><span data-stu-id="55f00-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="55f00-120">activityName</span><span class="sxs-lookup"><span data-stu-id="55f00-120">activityName</span></span>|<span data-ttu-id="55f00-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="55f00-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="55f00-122">Wartość domyślna to *, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="55f00-122">The default is *, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="55f00-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="55f00-123">faultHandlerActivityName</span></span>|<span data-ttu-id="55f00-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="55f00-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55f00-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="55f00-125">Child Elements</span></span>  
 <span data-ttu-id="55f00-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="55f00-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55f00-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="55f00-127">Parent Elements</span></span>  
  
|<span data-ttu-id="55f00-128">Element</span><span class="sxs-lookup"><span data-stu-id="55f00-128">Element</span></span>|<span data-ttu-id="55f00-129">Opis</span><span class="sxs-lookup"><span data-stu-id="55f00-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55f00-130">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="55f00-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="55f00-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="55f00-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="55f00-132">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="55f00-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55f00-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55f00-133">See Also</span></span>  
 <span data-ttu-id="55f00-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55f00-134"><xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="55f00-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="55f00-135"><xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="55f00-136">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="55f00-136">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="55f00-137">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="55f00-137">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
