---
title: '&lt;faultPropagationQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: d85f66a7-e7b0-4dbb-83cc-89fa06fc9161
ms.openlocfilehash: 5db043b5d4d150628df386dafb6e7bd351a0a28a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754007"
---
# <a name="ltfaultpropagationqueriesgt-of-wcf"></a><span data-ttu-id="e8856-102">&lt;faultPropagationQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="e8856-102">&lt;faultPropagationQueries&gt; of WCF</span></span>
<span data-ttu-id="e8856-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e8856-103">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e8856-104">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="e8856-104">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="e8856-105">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e8856-105">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="e8856-106">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="e8856-106">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="e8856-107">Aby uzyskać więcej informacji na zapytania dotyczące profilu śledzenia, zobacz [śledzenia profile](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="e8856-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="e8856-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e8856-108">\<system.serviceModel></span></span>  
<span data-ttu-id="e8856-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e8856-109">\<tracking></span></span>  
<span data-ttu-id="e8856-110">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e8856-110">\<trackingProfile></span></span>  
<span data-ttu-id="e8856-111">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e8856-111">\<workflow></span></span>  
<span data-ttu-id="e8856-112">\<faultPropagationQueries ></span><span class="sxs-lookup"><span data-stu-id="e8856-112">\<faultPropagationQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8856-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8856-113">Syntax</span></span>  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e8856-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8856-114">Attributes and Elements</span></span>  
 <span data-ttu-id="e8856-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8856-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8856-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8856-116">Attributes</span></span>  
 <span data-ttu-id="e8856-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="e8856-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e8856-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8856-118">Child Elements</span></span>  
  
|<span data-ttu-id="e8856-119">Element</span><span class="sxs-lookup"><span data-stu-id="e8856-119">Element</span></span>|<span data-ttu-id="e8856-120">Opis</span><span class="sxs-lookup"><span data-stu-id="e8856-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8856-121">\<faultPropagationQuery ></span><span class="sxs-lookup"><span data-stu-id="e8856-121">\<faultPropagationQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="e8856-122">Kwerenda, która służy do śledzenia Obsługa błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="e8856-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="e8856-123">To zdarzenie występuje zawsze FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="e8856-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e8856-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8856-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e8856-125">Element</span><span class="sxs-lookup"><span data-stu-id="e8856-125">Element</span></span>|<span data-ttu-id="e8856-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e8856-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8856-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e8856-127">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e8856-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e8856-128">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8856-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8856-129">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="e8856-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e8856-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="e8856-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e8856-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
