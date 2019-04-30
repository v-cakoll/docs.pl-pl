---
title: <faultPropagationQueries> w WCF
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: bc016827c5bb243bc83dbb53c1eda7eec1bfd8c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704014"
---
# <a name="faultpropagationqueries-of-wcf"></a><span data-ttu-id="59650-102">\<faultPropagationQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="59650-102">\<faultPropagationQueries> of WCF</span></span>

<span data-ttu-id="59650-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="59650-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="59650-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="59650-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="59650-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="59650-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="59650-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="59650-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="59650-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="59650-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="59650-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="59650-108">\<system.serviceModel></span></span>  
<span data-ttu-id="59650-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="59650-109">\<tracking></span></span>  
<span data-ttu-id="59650-110">\<profiles></span><span class="sxs-lookup"><span data-stu-id="59650-110">\<profiles></span></span>  
<span data-ttu-id="59650-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="59650-111">\<trackingProfile></span></span>  
<span data-ttu-id="59650-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="59650-112">\<workflow></span></span>  
<span data-ttu-id="59650-113">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="59650-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59650-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="59650-114">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <faultPropagationQueries>
          <faultPropagationQuery faultSourceActivityName="String"
                                 faultHandlerActivityName="String"/>
        </faultPropagationQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59650-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="59650-115">Attributes and elements</span></span>

<span data-ttu-id="59650-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59650-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="59650-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="59650-117">Attributes</span></span>

<span data-ttu-id="59650-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="59650-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="59650-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="59650-119">Child elements</span></span>

|<span data-ttu-id="59650-120">Element</span><span class="sxs-lookup"><span data-stu-id="59650-120">Element</span></span>|<span data-ttu-id="59650-121">Opis</span><span class="sxs-lookup"><span data-stu-id="59650-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59650-122">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="59650-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="59650-123">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="59650-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="59650-124">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="59650-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59650-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="59650-125">Parent elements</span></span>  
  
|<span data-ttu-id="59650-126">Element</span><span class="sxs-lookup"><span data-stu-id="59650-126">Element</span></span>|<span data-ttu-id="59650-127">Opis</span><span class="sxs-lookup"><span data-stu-id="59650-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59650-128">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="59650-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="59650-129">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="59650-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59650-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59650-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="59650-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="59650-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="59650-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="59650-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
