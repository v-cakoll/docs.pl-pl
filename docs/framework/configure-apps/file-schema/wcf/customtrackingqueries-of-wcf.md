---
title: <customTrackingQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: abc0c7dfb426338ec6bca61b0a4b87754bb63588
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925936"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="ec3f1-102">\<customTrackingQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="ec3f1-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="ec3f1-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ec3f1-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ec3f1-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ec3f1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="ec3f1-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ec3f1-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ec3f1-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ec3f1-107">\<tracking></span></span>  
<span data-ttu-id="ec3f1-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="ec3f1-108">\<profiles></span></span>  
<span data-ttu-id="ec3f1-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ec3f1-109">\<trackingProfile></span></span>  
<span data-ttu-id="ec3f1-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ec3f1-110">\<workflow></span></span>  
<span data-ttu-id="ec3f1-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="ec3f1-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec3f1-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec3f1-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec3f1-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec3f1-113">Attributes and elements</span></span>

<span data-ttu-id="ec3f1-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec3f1-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec3f1-115">Attributes</span></span>

<span data-ttu-id="ec3f1-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ec3f1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec3f1-117">Child elements</span></span>
  
|<span data-ttu-id="ec3f1-118">Element</span><span class="sxs-lookup"><span data-stu-id="ec3f1-118">Element</span></span>|<span data-ttu-id="ec3f1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ec3f1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec3f1-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ec3f1-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="ec3f1-121">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec3f1-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec3f1-122">Parent elements</span></span>  
  
|<span data-ttu-id="ec3f1-123">Element</span><span class="sxs-lookup"><span data-stu-id="ec3f1-123">Element</span></span>|<span data-ttu-id="ec3f1-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ec3f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec3f1-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ec3f1-125">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="ec3f1-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ec3f1-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ec3f1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec3f1-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ec3f1-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ec3f1-128">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ec3f1-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ec3f1-129">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
