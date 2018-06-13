---
title: '&lt;faultPropagationQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 5fd6ffc9560247089c7fbb60b0e5a7d3a417ea6f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755152"
---
# <a name="ltfaultpropagationqueriesgt"></a><span data-ttu-id="a9920-102">&lt;faultPropagationQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="a9920-102">&lt;faultPropagationQueries&gt;</span></span>
<span data-ttu-id="a9920-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a9920-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a9920-104">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="a9920-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="a9920-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a9920-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="a9920-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="a9920-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="a9920-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="a9920-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="a9920-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a9920-108">\<system.serviceModel></span></span>  
<span data-ttu-id="a9920-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="a9920-109">\<tracking></span></span>  
<span data-ttu-id="a9920-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="a9920-110">\<trackingProfile></span></span>  
<span data-ttu-id="a9920-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a9920-111">\<workflow></span></span>  
<span data-ttu-id="a9920-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="a9920-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9920-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9920-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9920-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a9920-114">Attributes and Elements</span></span>  
 <span data-ttu-id="a9920-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a9920-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9920-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a9920-116">Attributes</span></span>  
 <span data-ttu-id="a9920-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="a9920-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a9920-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a9920-118">Child Elements</span></span>  
  
|<span data-ttu-id="a9920-119">Element</span><span class="sxs-lookup"><span data-stu-id="a9920-119">Element</span></span>|<span data-ttu-id="a9920-120">Opis</span><span class="sxs-lookup"><span data-stu-id="a9920-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9920-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="a9920-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="a9920-122">Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="a9920-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="a9920-123">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="a9920-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a9920-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a9920-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a9920-125">Element</span><span class="sxs-lookup"><span data-stu-id="a9920-125">Element</span></span>|<span data-ttu-id="a9920-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a9920-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a9920-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="a9920-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="a9920-128">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy, identyfikowane przez **obiektu activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="a9920-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9920-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9920-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="a9920-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a9920-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="a9920-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="a9920-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
