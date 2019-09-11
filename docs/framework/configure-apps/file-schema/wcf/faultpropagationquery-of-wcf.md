---
title: <faultPropagationQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855334"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="50f38-102">\<faultPropagationQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="50f38-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="50f38-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="50f38-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="50f38-104">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="50f38-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="50f38-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="50f38-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="50f38-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="50f38-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="50f38-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="50f38-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="50f38-108">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="50f38-109">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="50f38-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="50f38-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="50f38-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="50f38-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="50f38-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="50f38-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<faultPropagationQueries >** ](faultpropagationqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="50f38-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)</span></span>\
<span data-ttu-id="50f38-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<faultPropagationQuery >**</span><span class="sxs-lookup"><span data-stu-id="50f38-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="50f38-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="50f38-116">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="50f38-117">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50f38-117">Attributes and elements</span></span>

<span data-ttu-id="50f38-118">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50f38-118">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="50f38-119">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50f38-119">Attributes</span></span>

|<span data-ttu-id="50f38-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="50f38-120">Attribute</span></span>|<span data-ttu-id="50f38-121">Opis</span><span class="sxs-lookup"><span data-stu-id="50f38-121">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="50f38-122">Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd.</span><span class="sxs-lookup"><span data-stu-id="50f38-122">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="50f38-123">Wartość domyślna to \*, co oznacza, że rekordy propagacji błędów są zwracane dla wszystkich działań.</span><span class="sxs-lookup"><span data-stu-id="50f38-123">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="50f38-124">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="50f38-124">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="50f38-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50f38-125">Child elements</span></span>

<span data-ttu-id="50f38-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="50f38-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="50f38-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50f38-127">Parent elements</span></span>

|<span data-ttu-id="50f38-128">Element</span><span class="sxs-lookup"><span data-stu-id="50f38-128">Element</span></span>|<span data-ttu-id="50f38-129">Opis</span><span class="sxs-lookup"><span data-stu-id="50f38-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="50f38-130">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="50f38-130">\<faultPropagationQueries></span></span>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="50f38-131">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="50f38-131">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="50f38-132">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="50f38-132">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="50f38-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50f38-133">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="50f38-134">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="50f38-134">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="50f38-135">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="50f38-135">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
