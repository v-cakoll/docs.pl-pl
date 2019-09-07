---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398717"
---
# <a name="faultpropagationquery"></a><span data-ttu-id="48b17-101">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="48b17-101">\<faultPropagationQuery></span></span>

<span data-ttu-id="48b17-102">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="48b17-102">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="48b17-103">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="48b17-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="48b17-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="48b17-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="48b17-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="48b17-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="48b17-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="48b17-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="48b17-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48b17-108">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="48b17-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="48b17-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="48b17-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="48b17-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries.md)</span><span class="sxs-lookup"><span data-stu-id="48b17-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)</span></span>\
<span data-ttu-id="48b17-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="48b17-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>

## <a name="syntax"></a><span data-ttu-id="48b17-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="48b17-114">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="48b17-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48b17-115">Attributes and Elements</span></span>

<span data-ttu-id="48b17-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48b17-116">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="48b17-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48b17-117">Attributes</span></span>

|<span data-ttu-id="48b17-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="48b17-118">Attribute</span></span>|<span data-ttu-id="48b17-119">Opis</span><span class="sxs-lookup"><span data-stu-id="48b17-119">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="48b17-120">activityName</span><span class="sxs-lookup"><span data-stu-id="48b17-120">activityName</span></span>|<span data-ttu-id="48b17-121">Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd.</span><span class="sxs-lookup"><span data-stu-id="48b17-121">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="48b17-122">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="48b17-122">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="48b17-123">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="48b17-123">faultHandlerActivityName</span></span>|<span data-ttu-id="48b17-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="48b17-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="48b17-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48b17-125">Child Elements</span></span>

<span data-ttu-id="48b17-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="48b17-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="48b17-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48b17-127">Parent Elements</span></span>

|<span data-ttu-id="48b17-128">Element</span><span class="sxs-lookup"><span data-stu-id="48b17-128">Element</span></span>|<span data-ttu-id="48b17-129">Opis</span><span class="sxs-lookup"><span data-stu-id="48b17-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="48b17-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="48b17-130">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="48b17-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="48b17-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="48b17-132">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="48b17-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="48b17-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48b17-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="48b17-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="48b17-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="48b17-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="48b17-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
