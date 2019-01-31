---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 0424c01397a95803b9e8502d90a55d1bd4c3b5e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269396"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="77644-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="77644-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="77644-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="77644-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="77644-103">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="77644-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="77644-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="77644-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="77644-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="77644-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="77644-106">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="77644-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="77644-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="77644-107">\<system.serviceModel></span></span>  
<span data-ttu-id="77644-108">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="77644-108">\<tracking></span></span>  
<span data-ttu-id="77644-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="77644-109">\<trackingProfile></span></span>  
<span data-ttu-id="77644-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="77644-110">\<workflow></span></span>  
<span data-ttu-id="77644-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="77644-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77644-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="77644-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77644-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="77644-113">Attributes and Elements</span></span>  
 <span data-ttu-id="77644-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="77644-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77644-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="77644-115">Attributes</span></span>  
 <span data-ttu-id="77644-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="77644-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="77644-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="77644-117">Child Elements</span></span>  
  
|<span data-ttu-id="77644-118">Element</span><span class="sxs-lookup"><span data-stu-id="77644-118">Element</span></span>|<span data-ttu-id="77644-119">Opis</span><span class="sxs-lookup"><span data-stu-id="77644-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77644-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="77644-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="77644-121">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="77644-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="77644-122">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="77644-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77644-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="77644-123">Parent Elements</span></span>  
  
|<span data-ttu-id="77644-124">Element</span><span class="sxs-lookup"><span data-stu-id="77644-124">Element</span></span>|<span data-ttu-id="77644-125">Opis</span><span class="sxs-lookup"><span data-stu-id="77644-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77644-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="77644-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="77644-127">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="77644-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77644-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77644-128">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="77644-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="77644-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="77644-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="77644-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
