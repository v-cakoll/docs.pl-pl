---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679362"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="34d6d-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="34d6d-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="34d6d-102">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34d6d-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="34d6d-103">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34d6d-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="34d6d-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34d6d-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="34d6d-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="34d6d-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="34d6d-106">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="34d6d-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="34d6d-107">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="34d6d-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="34d6d-108">\<Śledzenie > \\</span><span class="sxs-lookup"><span data-stu-id="34d6d-108">\<tracking>\\</span></span>
<span data-ttu-id="34d6d-109">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="34d6d-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="34d6d-110">\<przepływ pracy > \\</span><span class="sxs-lookup"><span data-stu-id="34d6d-110">\<workflow>\\</span></span>
<span data-ttu-id="34d6d-111">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="34d6d-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="34d6d-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="34d6d-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="34d6d-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="34d6d-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="34d6d-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34d6d-114">Attributes and Elements</span></span>

<span data-ttu-id="34d6d-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34d6d-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="34d6d-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34d6d-116">Attributes</span></span>

|<span data-ttu-id="34d6d-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34d6d-117">Attribute</span></span>|<span data-ttu-id="34d6d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="34d6d-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="34d6d-119">activityName</span><span class="sxs-lookup"><span data-stu-id="34d6d-119">activityName</span></span>|<span data-ttu-id="34d6d-120">Ciąg określający nazwę działanie procedury obsługi błędów, błędów.</span><span class="sxs-lookup"><span data-stu-id="34d6d-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="34d6d-121">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="34d6d-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="34d6d-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="34d6d-122">faultHandlerActivityName</span></span>|<span data-ttu-id="34d6d-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="34d6d-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="34d6d-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34d6d-124">Child Elements</span></span>

<span data-ttu-id="34d6d-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="34d6d-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34d6d-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34d6d-126">Parent Elements</span></span>

|<span data-ttu-id="34d6d-127">Element</span><span class="sxs-lookup"><span data-stu-id="34d6d-127">Element</span></span>|<span data-ttu-id="34d6d-128">Opis</span><span class="sxs-lookup"><span data-stu-id="34d6d-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="34d6d-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="34d6d-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="34d6d-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="34d6d-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="34d6d-131">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="34d6d-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="34d6d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34d6d-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="34d6d-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="34d6d-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="34d6d-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="34d6d-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
