---
title: '&lt;faultPropagationQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 1da2a95d27756296aab5a205a90fb028508c4b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601808"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="995bc-102">&lt;faultPropagationQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="995bc-102">&lt;faultPropagationQuery&gt; of WCF</span></span>

<span data-ttu-id="995bc-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="995bc-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="995bc-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="995bc-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="995bc-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="995bc-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="995bc-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="995bc-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="995bc-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="995bc-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="995bc-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="995bc-108">\<system.serviceModel></span></span>  
<span data-ttu-id="995bc-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="995bc-109">\<tracking></span></span>  
<span data-ttu-id="995bc-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="995bc-110">\<profiles></span></span>  
<span data-ttu-id="995bc-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="995bc-111">\<trackingProfile></span></span>  
<span data-ttu-id="995bc-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="995bc-112">\<workflow></span></span>  
<span data-ttu-id="995bc-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="995bc-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="995bc-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="995bc-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995bc-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="995bc-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String" />
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="995bc-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="995bc-116">Attributes and elements</span></span>

<span data-ttu-id="995bc-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="995bc-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="995bc-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="995bc-118">Attributes</span></span>  
  
|<span data-ttu-id="995bc-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="995bc-119">Attribute</span></span>|<span data-ttu-id="995bc-120">Opis</span><span class="sxs-lookup"><span data-stu-id="995bc-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="995bc-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="995bc-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="995bc-122">Wartość domyślna to \*, co oznacza, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="995bc-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="995bc-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="995bc-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="995bc-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="995bc-124">Child elements</span></span>

<span data-ttu-id="995bc-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="995bc-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="995bc-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="995bc-126">Parent elements</span></span>  
  
|<span data-ttu-id="995bc-127">Element</span><span class="sxs-lookup"><span data-stu-id="995bc-127">Element</span></span>|<span data-ttu-id="995bc-128">Opis</span><span class="sxs-lookup"><span data-stu-id="995bc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="995bc-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="995bc-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="995bc-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="995bc-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="995bc-131">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="995bc-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="995bc-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="995bc-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="995bc-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="995bc-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="995bc-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="995bc-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
