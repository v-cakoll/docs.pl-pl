---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204045"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="c65c3-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c65c3-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="c65c3-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c65c3-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c65c3-103">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c65c3-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="c65c3-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c65c3-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="c65c3-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="c65c3-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="c65c3-106">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c65c3-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="c65c3-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c65c3-107">\<system.serviceModel></span></span>  
<span data-ttu-id="c65c3-108">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="c65c3-108">\<tracking></span></span>  
<span data-ttu-id="c65c3-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="c65c3-109">\<trackingProfile></span></span>  
<span data-ttu-id="c65c3-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="c65c3-110">\<workflow></span></span>  
<span data-ttu-id="c65c3-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="c65c3-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65c3-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="c65c3-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65c3-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c65c3-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c65c3-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c65c3-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65c3-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c65c3-115">Attributes</span></span>  
 <span data-ttu-id="c65c3-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="c65c3-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c65c3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c65c3-117">Child Elements</span></span>  
  
|<span data-ttu-id="c65c3-118">Element</span><span class="sxs-lookup"><span data-stu-id="c65c3-118">Element</span></span>|<span data-ttu-id="c65c3-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c65c3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65c3-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="c65c3-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="c65c3-121">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="c65c3-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="c65c3-122">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c65c3-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c65c3-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c65c3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c65c3-124">Element</span><span class="sxs-lookup"><span data-stu-id="c65c3-124">Element</span></span>|<span data-ttu-id="c65c3-125">Opis</span><span class="sxs-lookup"><span data-stu-id="c65c3-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65c3-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="c65c3-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="c65c3-127">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="c65c3-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c65c3-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c65c3-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="c65c3-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c65c3-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c65c3-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c65c3-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
