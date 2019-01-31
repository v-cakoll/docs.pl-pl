---
title: <faultPropagationQuery> w WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 1670f8fdf72bc202a4a595034f3818ab43b11be6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276058"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="015fa-102">\<faultPropagationQuery > w WCF</span><span class="sxs-lookup"><span data-stu-id="015fa-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="015fa-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="015fa-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="015fa-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="015fa-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="015fa-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="015fa-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="015fa-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="015fa-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="015fa-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="015fa-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="015fa-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="015fa-108">\<system.serviceModel></span></span>  
<span data-ttu-id="015fa-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="015fa-109">\<tracking></span></span>  
<span data-ttu-id="015fa-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="015fa-110">\<profiles></span></span>  
<span data-ttu-id="015fa-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="015fa-111">\<trackingProfile></span></span>  
<span data-ttu-id="015fa-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="015fa-112">\<workflow></span></span>  
<span data-ttu-id="015fa-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="015fa-113">\<faultPropagationQueries></span></span>  
<span data-ttu-id="015fa-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="015fa-114">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="015fa-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="015fa-115">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="015fa-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="015fa-116">Attributes and elements</span></span>

<span data-ttu-id="015fa-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="015fa-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="015fa-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="015fa-118">Attributes</span></span>  
  
|<span data-ttu-id="015fa-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="015fa-119">Attribute</span></span>|<span data-ttu-id="015fa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="015fa-120">Description</span></span>|  
|---------------|-----------------|  
|`faultSourceActivityName`|<span data-ttu-id="015fa-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="015fa-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="015fa-122">Wartość domyślna to \*, co oznacza, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="015fa-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|`faultHandlerActivityName`|<span data-ttu-id="015fa-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="015fa-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="015fa-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="015fa-124">Child elements</span></span>

<span data-ttu-id="015fa-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="015fa-125">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="015fa-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="015fa-126">Parent elements</span></span>  
  
|<span data-ttu-id="015fa-127">Element</span><span class="sxs-lookup"><span data-stu-id="015fa-127">Element</span></span>|<span data-ttu-id="015fa-128">Opis</span><span class="sxs-lookup"><span data-stu-id="015fa-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="015fa-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="015fa-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="015fa-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="015fa-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="015fa-131">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="015fa-131">This event occurs each time a FaultHandler processes a fault.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="015fa-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="015fa-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="015fa-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="015fa-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="015fa-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="015fa-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
