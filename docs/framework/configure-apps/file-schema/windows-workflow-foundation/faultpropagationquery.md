---
title: '&lt;faultPropagationQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: a91a6f61b39a780ed48ad8d5f5e0dfb9ef60da39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538339"
---
# <a name="ltfaultpropagationquerygt"></a><span data-ttu-id="3edcd-102">&lt;faultPropagationQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="3edcd-102">&lt;faultPropagationQuery&gt;</span></span>
<span data-ttu-id="3edcd-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="3edcd-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3edcd-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3edcd-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="3edcd-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="3edcd-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="3edcd-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="3edcd-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="3edcd-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="3edcd-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="3edcd-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3edcd-108">\<system.serviceModel></span></span>  
<span data-ttu-id="3edcd-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="3edcd-109">\<tracking></span></span>  
<span data-ttu-id="3edcd-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3edcd-110">\<trackingProfile></span></span>  
<span data-ttu-id="3edcd-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="3edcd-111">\<workflow></span></span>  
<span data-ttu-id="3edcd-112">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="3edcd-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="3edcd-113">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="3edcd-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3edcd-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="3edcd-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3edcd-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3edcd-115">Attributes and Elements</span></span>  
 <span data-ttu-id="3edcd-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3edcd-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3edcd-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3edcd-117">Attributes</span></span>  
  
|<span data-ttu-id="3edcd-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3edcd-118">Attribute</span></span>|<span data-ttu-id="3edcd-119">Opis</span><span class="sxs-lookup"><span data-stu-id="3edcd-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3edcd-120">activityName</span><span class="sxs-lookup"><span data-stu-id="3edcd-120">activityName</span></span>|<span data-ttu-id="3edcd-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="3edcd-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="3edcd-122">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="3edcd-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="3edcd-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="3edcd-123">faultHandlerActivityName</span></span>|<span data-ttu-id="3edcd-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="3edcd-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3edcd-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3edcd-125">Child Elements</span></span>  
 <span data-ttu-id="3edcd-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="3edcd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3edcd-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3edcd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3edcd-128">Element</span><span class="sxs-lookup"><span data-stu-id="3edcd-128">Element</span></span>|<span data-ttu-id="3edcd-129">Opis</span><span class="sxs-lookup"><span data-stu-id="3edcd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3edcd-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="3edcd-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="3edcd-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="3edcd-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="3edcd-132">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3edcd-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3edcd-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3edcd-133">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3edcd-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3edcd-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3edcd-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="3edcd-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
