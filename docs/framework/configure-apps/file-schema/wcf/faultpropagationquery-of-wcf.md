---
title: <faultPropagationQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: 6ba6478ca500c0a8ef150966a97898f8743ffdf8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925632"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="a7a87-102">\<faultPropagationQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="a7a87-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="a7a87-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a7a87-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a7a87-104">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="a7a87-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a7a87-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a7a87-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a7a87-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="a7a87-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="a7a87-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a7a87-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="a7a87-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a7a87-108">\<system.serviceModel></span></span>\
<span data-ttu-id="a7a87-109">\<Śledzenie > </span><span class="sxs-lookup"><span data-stu-id="a7a87-109">\<tracking></span></span>\
<span data-ttu-id="a7a87-110">\<Profile > </span><span class="sxs-lookup"><span data-stu-id="a7a87-110">\<profiles></span></span>\
<span data-ttu-id="a7a87-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a7a87-111">\<trackingProfile></span></span>\
<span data-ttu-id="a7a87-112">\<przepływ pracy > </span><span class="sxs-lookup"><span data-stu-id="a7a87-112">\<workflow></span></span>\
<span data-ttu-id="a7a87-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="a7a87-113">\<faultPropagationQueries></span></span>\
<span data-ttu-id="a7a87-114">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="a7a87-114">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="a7a87-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7a87-115">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="a7a87-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7a87-116">Attributes and elements</span></span>

<span data-ttu-id="a7a87-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7a87-117">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a7a87-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7a87-118">Attributes</span></span>

|<span data-ttu-id="a7a87-119">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7a87-119">Attribute</span></span>|<span data-ttu-id="a7a87-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a7a87-120">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="a7a87-121">Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd.</span><span class="sxs-lookup"><span data-stu-id="a7a87-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="a7a87-122">Wartość domyślna to \*, co oznacza, że rekordy propagacji błędów są zwracane dla wszystkich działań.</span><span class="sxs-lookup"><span data-stu-id="a7a87-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="a7a87-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="a7a87-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a7a87-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7a87-124">Child elements</span></span>

<span data-ttu-id="a7a87-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="a7a87-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a7a87-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7a87-126">Parent elements</span></span>

|<span data-ttu-id="a7a87-127">Element</span><span class="sxs-lookup"><span data-stu-id="a7a87-127">Element</span></span>|<span data-ttu-id="a7a87-128">Opis</span><span class="sxs-lookup"><span data-stu-id="a7a87-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a7a87-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="a7a87-129">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="a7a87-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a7a87-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a7a87-131">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="a7a87-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a7a87-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7a87-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="a7a87-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a7a87-133">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="a7a87-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a7a87-134">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
