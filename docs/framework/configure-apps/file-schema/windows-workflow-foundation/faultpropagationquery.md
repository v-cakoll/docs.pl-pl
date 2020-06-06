---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: 6b43a570b4d4534adce1ef5ab394849651e3ac0e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398717"
---
# \<faultPropagationQuery>

<span data-ttu-id="c66b2-101">Reprezentuje zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c66b2-101">Represents a query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c66b2-102">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="c66b2-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c66b2-103">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c66b2-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c66b2-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="c66b2-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>

 <span data-ttu-id="c66b2-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c66b2-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<faultPropagationQueries>**](faultpropagationqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQuery>**

## <a name="syntax"></a><span data-ttu-id="c66b2-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c66b2-106">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="c66b2-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c66b2-107">Attributes and Elements</span></span>

<span data-ttu-id="c66b2-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c66b2-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c66b2-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c66b2-109">Attributes</span></span>

|<span data-ttu-id="c66b2-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c66b2-110">Attribute</span></span>|<span data-ttu-id="c66b2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c66b2-111">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c66b2-112">activityName</span><span class="sxs-lookup"><span data-stu-id="c66b2-112">activityName</span></span>|<span data-ttu-id="c66b2-113">Ciąg określający nazwę działania procedury obsługi błędu, które propaguje błąd.</span><span class="sxs-lookup"><span data-stu-id="c66b2-113">A string that specifies the name of the fault handler activity that propagated the fault.</span></span> <span data-ttu-id="c66b2-114">Wartość domyślna to \*, która wskazuje, że dla wszystkich działań zwracane są rekordy propagacji błędów.</span><span class="sxs-lookup"><span data-stu-id="c66b2-114">The default is \*, which indicates that fault propagation records are returned for all activities.</span></span>|
|<span data-ttu-id="c66b2-115">faultHandlerActivityName</span><span class="sxs-lookup"><span data-stu-id="c66b2-115">faultHandlerActivityName</span></span>|<span data-ttu-id="c66b2-116">Ciąg określający nazwę czynności, która została źródła błędu.</span><span class="sxs-lookup"><span data-stu-id="c66b2-116">A string that specifies the name of the activity that was the source of the fault.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c66b2-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c66b2-117">Child Elements</span></span>

<span data-ttu-id="c66b2-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="c66b2-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c66b2-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c66b2-119">Parent Elements</span></span>

|<span data-ttu-id="c66b2-120">Element</span><span class="sxs-lookup"><span data-stu-id="c66b2-120">Element</span></span>|<span data-ttu-id="c66b2-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c66b2-121">Description</span></span>|
|-------------|-----------------|
|[\<faultPropagationQueries>](faultpropagationqueries.md)|<span data-ttu-id="c66b2-122">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c66b2-122">Represents a list of configuration elements that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c66b2-123">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="c66b2-123">This event occurs each time a FaultHandler processes a fault.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c66b2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c66b2-124">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c66b2-125">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c66b2-125">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c66b2-126">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c66b2-126">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
