---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794553"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="41b71-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="41b71-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="41b71-102">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="41b71-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="41b71-103">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41b71-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="41b71-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="41b71-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="41b71-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="41b71-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="41b71-106">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="41b71-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="41b71-107">\<system.serviceModel>\\</span><span class="sxs-lookup"><span data-stu-id="41b71-107">\<system.serviceModel>\\</span></span>
<span data-ttu-id="41b71-108">\<Śledzenie > \\</span><span class="sxs-lookup"><span data-stu-id="41b71-108">\<tracking>\\</span></span>
<span data-ttu-id="41b71-109">\<trackingProfile>\\</span><span class="sxs-lookup"><span data-stu-id="41b71-109">\<trackingProfile>\\</span></span>
<span data-ttu-id="41b71-110">\<przepływ pracy > \\</span><span class="sxs-lookup"><span data-stu-id="41b71-110">\<workflow>\\</span></span>
<span data-ttu-id="41b71-111">\<faultPropagationQueries>\\</span><span class="sxs-lookup"><span data-stu-id="41b71-111">\<faultPropagationQueries>\\</span></span>
<span data-ttu-id="41b71-112">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="41b71-112">\<faultPropagationQuery></span></span>

## <a name="syntax"></a><span data-ttu-id="41b71-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="41b71-113">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="41b71-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="41b71-114">Attributes and Elements</span></span>

<span data-ttu-id="41b71-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="41b71-115">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="41b71-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41b71-116">Attributes</span></span>

|<span data-ttu-id="41b71-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="41b71-117">Attribute</span></span>|<span data-ttu-id="41b71-118">Opis</span><span class="sxs-lookup"><span data-stu-id="41b71-118">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="41b71-119">activityName</span><span class="sxs-lookup"><span data-stu-id="41b71-119">activityName</span></span>|<span data-ttu-id="41b71-120">Ciąg określający nazwę działanie procedury obsługi błędów, błędów.</span><span class="sxs-lookup"><span data-stu-id="41b71-120">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="41b71-121">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="41b71-121">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="41b71-122">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="41b71-122">faultHandlerActivityName</span></span>|<span data-ttu-id="41b71-123">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="41b71-123">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="41b71-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="41b71-124">Child Elements</span></span>

<span data-ttu-id="41b71-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="41b71-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="41b71-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="41b71-126">Parent Elements</span></span>

|<span data-ttu-id="41b71-127">Element</span><span class="sxs-lookup"><span data-stu-id="41b71-127">Element</span></span>|<span data-ttu-id="41b71-128">Opis</span><span class="sxs-lookup"><span data-stu-id="41b71-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41b71-129">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="41b71-129">\<faultPropagationQueries></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|<span data-ttu-id="41b71-130">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="41b71-130">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="41b71-131">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="41b71-131">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="41b71-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41b71-132">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="41b71-133">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="41b71-133">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="41b71-134">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="41b71-134">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
