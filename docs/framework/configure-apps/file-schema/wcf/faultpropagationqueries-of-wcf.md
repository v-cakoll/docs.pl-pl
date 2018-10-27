---
title: '&lt;faultPropagationQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 1db99a8d80fad5c0eca93777d87047b43371d048
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044414"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="9ec3c-102">&lt;faultPropagationQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="9ec3c-102">&lt;faultPropagationQueries&gt; of WCF</span></span>

<span data-ttu-id="9ec3c-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9ec3c-104">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="9ec3c-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="9ec3c-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
<span data-ttu-id="9ec3c-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="9ec3c-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="9ec3c-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9ec3c-108">\<system.serviceModel></span></span>  
<span data-ttu-id="9ec3c-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-109">\<tracking></span></span>  
<span data-ttu-id="9ec3c-110">\<profile ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-110">\<profiles></span></span>  
<span data-ttu-id="9ec3c-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9ec3c-111">\<trackingProfile></span></span>  
<span data-ttu-id="9ec3c-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-112">\<workflow></span></span>  
<span data-ttu-id="9ec3c-113">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-113">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec3c-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ec3c-114">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="9ec3c-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ec3c-115">Attributes and elements</span></span>

<span data-ttu-id="9ec3c-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="9ec3c-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ec3c-117">Attributes</span></span>

<span data-ttu-id="9ec3c-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-118">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9ec3c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ec3c-119">Child elements</span></span>

|<span data-ttu-id="9ec3c-120">Element</span><span class="sxs-lookup"><span data-stu-id="9ec3c-120">Element</span></span>|<span data-ttu-id="9ec3c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="9ec3c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ec3c-122">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-122">\<faultPropagationQuery></span></span>](faultpropagationquery-of-wcf.md)|<span data-ttu-id="9ec3c-123">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="9ec3c-124">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-124">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ec3c-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ec3c-125">Parent elements</span></span>  
  
|<span data-ttu-id="9ec3c-126">Element</span><span class="sxs-lookup"><span data-stu-id="9ec3c-126">Element</span></span>|<span data-ttu-id="9ec3c-127">Opis</span><span class="sxs-lookup"><span data-stu-id="9ec3c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ec3c-128">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9ec3c-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9ec3c-129">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ec3c-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ec3c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ec3c-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9ec3c-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9ec3c-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9ec3c-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9ec3c-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
