---
title: '&lt;faultPropagationQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: df7119363e94a070bb898c984c12cf82755c3407
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087703"
---
# <a name="ltfaultpropagationquerygt-of-wcf"></a><span data-ttu-id="30aff-102">&lt;faultPropagationQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="30aff-102">&lt;faultPropagationQuery&gt; of WCF</span></span>
<span data-ttu-id="30aff-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="30aff-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="30aff-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="30aff-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="30aff-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="30aff-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="30aff-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="30aff-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="30aff-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="30aff-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="30aff-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="30aff-108">\<system.serviceModel></span></span>  
<span data-ttu-id="30aff-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="30aff-109">\<tracking></span></span>  
<span data-ttu-id="30aff-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="30aff-110">\<trackingProfile></span></span>  
<span data-ttu-id="30aff-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="30aff-111">\<workflow></span></span>  
<span data-ttu-id="30aff-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="30aff-112">\<faultPropagationQueries></span></span>  
<span data-ttu-id="30aff-113">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="30aff-113">\<faultPropagationQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30aff-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="30aff-114">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String"/>
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30aff-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="30aff-115">Attributes and Elements</span></span>  
 <span data-ttu-id="30aff-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="30aff-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30aff-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="30aff-117">Attributes</span></span>  
  
|<span data-ttu-id="30aff-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="30aff-118">Attribute</span></span>|<span data-ttu-id="30aff-119">Opis</span><span class="sxs-lookup"><span data-stu-id="30aff-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30aff-120">activityName</span><span class="sxs-lookup"><span data-stu-id="30aff-120">activityName</span></span>|<span data-ttu-id="30aff-121">Ciąg, który określa nazwę propagowane błędu działanie obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="30aff-121">A string that specifies the name of the fault hander activity that propagated the fault.</span></span> <span data-ttu-id="30aff-122">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="30aff-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|  
|<span data-ttu-id="30aff-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="30aff-123">faultHandlerActivityName</span></span>|<span data-ttu-id="30aff-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="30aff-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30aff-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="30aff-125">Child Elements</span></span>  
 <span data-ttu-id="30aff-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="30aff-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30aff-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="30aff-127">Parent Elements</span></span>  
  
|<span data-ttu-id="30aff-128">Element</span><span class="sxs-lookup"><span data-stu-id="30aff-128">Element</span></span>|<span data-ttu-id="30aff-129">Opis</span><span class="sxs-lookup"><span data-stu-id="30aff-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30aff-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="30aff-130">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="30aff-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="30aff-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="30aff-132">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="30aff-132">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30aff-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30aff-133">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="30aff-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="30aff-134">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="30aff-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="30aff-135">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
