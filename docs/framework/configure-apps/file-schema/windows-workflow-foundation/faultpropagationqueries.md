---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 402b938913575adfa9125b981dc2913680f07b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790159"
---
# <a name="faultpropagationqueries"></a><span data-ttu-id="f460e-101">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="f460e-101">\<faultPropagationQueries></span></span>
<span data-ttu-id="f460e-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="f460e-102">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f460e-103">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f460e-103">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="f460e-104">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="f460e-104">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="f460e-105">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="f460e-105">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="f460e-106">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="f460e-106">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="f460e-107">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f460e-107">\<system.serviceModel></span></span>  
<span data-ttu-id="f460e-108">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="f460e-108">\<tracking></span></span>  
<span data-ttu-id="f460e-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="f460e-109">\<trackingProfile></span></span>  
<span data-ttu-id="f460e-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f460e-110">\<workflow></span></span>  
<span data-ttu-id="f460e-111">\<faultPropagationQueries></span><span class="sxs-lookup"><span data-stu-id="f460e-111">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f460e-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="f460e-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f460e-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f460e-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f460e-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f460e-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f460e-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f460e-115">Attributes</span></span>  
 <span data-ttu-id="f460e-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f460e-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f460e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f460e-117">Child Elements</span></span>  
  
|<span data-ttu-id="f460e-118">Element</span><span class="sxs-lookup"><span data-stu-id="f460e-118">Element</span></span>|<span data-ttu-id="f460e-119">Opis</span><span class="sxs-lookup"><span data-stu-id="f460e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f460e-120">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="f460e-120">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="f460e-121">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="f460e-121">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="f460e-122">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f460e-122">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f460e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f460e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f460e-124">Element</span><span class="sxs-lookup"><span data-stu-id="f460e-124">Element</span></span>|<span data-ttu-id="f460e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f460e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f460e-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="f460e-126">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="f460e-127">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f460e-127">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f460e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f460e-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="f460e-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="f460e-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="f460e-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="f460e-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
