---
title: <faultPropagationQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: fabafbc8-3e45-4feb-8321-0725e9f4079c
ms.openlocfilehash: a6ef4e198caec4a1f21cedf2ff46d390aeaa2d3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855334"
---
# <a name="faultpropagationquery-of-wcf"></a><span data-ttu-id="dfde9-102">\<faultPropagationQuery>programu WCF</span><span class="sxs-lookup"><span data-stu-id="dfde9-102">\<faultPropagationQuery> of WCF</span></span>

<span data-ttu-id="dfde9-103">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="dfde9-103">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dfde9-104">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="dfde9-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="dfde9-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="dfde9-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="dfde9-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="dfde9-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

<span data-ttu-id="dfde9-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="dfde9-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**  

## <a name="syntax"></a><span data-ttu-id="dfde9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfde9-108">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="dfde9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dfde9-109">Attributes and elements</span></span>

<span data-ttu-id="dfde9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dfde9-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="dfde9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dfde9-111">Attributes</span></span>

|<span data-ttu-id="dfde9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dfde9-112">Attribute</span></span>|<span data-ttu-id="dfde9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="dfde9-113">Description</span></span>|
|---------------|-----------------|
|`faultSourceActivityName`|<span data-ttu-id="dfde9-114">Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd.</span><span class="sxs-lookup"><span data-stu-id="dfde9-114">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="dfde9-115">Wartość domyślna to \* , co oznacza, że rekordy propagacji błędów są zwracane dla wszystkich działań.</span><span class="sxs-lookup"><span data-stu-id="dfde9-115">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|`faultHandlerActivityName`|<span data-ttu-id="dfde9-116">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="dfde9-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="dfde9-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dfde9-117">Child elements</span></span>

<span data-ttu-id="dfde9-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="dfde9-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dfde9-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dfde9-119">Parent elements</span></span>

|<span data-ttu-id="dfde9-120">Element</span><span class="sxs-lookup"><span data-stu-id="dfde9-120">Element</span></span>|<span data-ttu-id="dfde9-121">Opis</span><span class="sxs-lookup"><span data-stu-id="dfde9-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries-of-wcf.md)|<span data-ttu-id="dfde9-122">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="dfde9-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="dfde9-123">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="dfde9-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="dfde9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfde9-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dfde9-125">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dfde9-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dfde9-126">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="dfde9-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
