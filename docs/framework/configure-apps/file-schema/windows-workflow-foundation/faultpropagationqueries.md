---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: b8052138a729fcba7cb158d81a63126f59e0c4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69988738"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="60ad1-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="60ad1-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="60ad1-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="60ad1-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="60ad1-103">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="60ad1-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="60ad1-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="60ad1-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="60ad1-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="60ad1-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="60ad1-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="60ad1-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="60ad1-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="60ad1-107">\<system.serviceModel></span></span>  
<span data-ttu-id="60ad1-108">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="60ad1-108">\<tracking></span></span>  
<span data-ttu-id="60ad1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="60ad1-109">\<trackingProfile></span></span>  
<span data-ttu-id="60ad1-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="60ad1-110">\<workflow></span></span>  
<span data-ttu-id="60ad1-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="60ad1-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ad1-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="60ad1-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60ad1-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="60ad1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="60ad1-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="60ad1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60ad1-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="60ad1-115">Attributes</span></span>  
 <span data-ttu-id="60ad1-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="60ad1-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="60ad1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="60ad1-117">Child Elements</span></span>  
  
|<span data-ttu-id="60ad1-118">Element</span><span class="sxs-lookup"><span data-stu-id="60ad1-118">Element</span></span>|<span data-ttu-id="60ad1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="60ad1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ad1-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="60ad1-120">\<faultPropagationQuery></span></span>](faultpropagationquery.md)|<span data-ttu-id="60ad1-121">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="60ad1-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="60ad1-122">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="60ad1-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60ad1-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="60ad1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="60ad1-124">Element</span><span class="sxs-lookup"><span data-stu-id="60ad1-124">Element</span></span>|<span data-ttu-id="60ad1-125">Opis</span><span class="sxs-lookup"><span data-stu-id="60ad1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ad1-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="60ad1-126">\<workflow></span></span>](workflow.md)|<span data-ttu-id="60ad1-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="60ad1-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60ad1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60ad1-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="60ad1-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="60ad1-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="60ad1-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="60ad1-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
