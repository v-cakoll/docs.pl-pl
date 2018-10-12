---
title: '&lt;faultPropagationQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: c3853c470a9243835e071d35008dfff5b885591d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123322"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="186a3-102">&lt;faultPropagationQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="186a3-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="186a3-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="186a3-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="186a3-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="186a3-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="186a3-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="186a3-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="186a3-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="186a3-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="186a3-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="186a3-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="186a3-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="186a3-108">\<system.serviceModel></span></span>  
<span data-ttu-id="186a3-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="186a3-109">\<tracking></span></span>  
<span data-ttu-id="186a3-110">\<profile ></span><span class="sxs-lookup"><span data-stu-id="186a3-110">\<profiles></span></span>  
<span data-ttu-id="186a3-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="186a3-111">\<trackingProfile></span></span>  
<span data-ttu-id="186a3-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="186a3-112">\<workflow></span></span>  
<span data-ttu-id="186a3-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="186a3-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="186a3-114">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="186a3-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186a3-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="186a3-115">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="186a3-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="186a3-116">Attributes and elements</span></span>

<span data-ttu-id="186a3-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="186a3-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="186a3-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="186a3-118">Attributes</span></span>  
  
|<span data-ttu-id="186a3-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="186a3-119">Attribute</span></span>|<span data-ttu-id="186a3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="186a3-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="186a3-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="186a3-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="186a3-122">Wartość domyślna to \*, co oznacza, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="186a3-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="186a3-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="186a3-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="186a3-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="186a3-124">Child elements</span></span>

<span data-ttu-id="186a3-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="186a3-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="186a3-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="186a3-126">Parent elements</span></span>  
  
|<span data-ttu-id="186a3-127">Element</span><span class="sxs-lookup"><span data-stu-id="186a3-127">Element</span></span>|<span data-ttu-id="186a3-128">Opis</span><span class="sxs-lookup"><span data-stu-id="186a3-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="186a3-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="186a3-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="186a3-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="186a3-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="186a3-131">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="186a3-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="186a3-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="186a3-132">See also</span></span>  
 
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="186a3-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="186a3-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="186a3-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="186a3-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
