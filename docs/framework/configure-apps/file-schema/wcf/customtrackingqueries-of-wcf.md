---
title: '&lt;customTrackingQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: f4f6186aa51ef1656f31fb0035f58a07e5c2447b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700796"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="26e26-102">&lt;customTrackingQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="26e26-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="26e26-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="26e26-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="26e26-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="26e26-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="26e26-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="26e26-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="26e26-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="26e26-106">\<system.serviceModel></span></span>  
<span data-ttu-id="26e26-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="26e26-107">\<tracking></span></span>  
<span data-ttu-id="26e26-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="26e26-108">\<profiles></span></span>  
<span data-ttu-id="26e26-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="26e26-109">\<trackingProfile></span></span>  
<span data-ttu-id="26e26-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="26e26-110">\<workflow></span></span>  
<span data-ttu-id="26e26-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="26e26-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26e26-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="26e26-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26e26-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26e26-113">Attributes and elements</span></span>

<span data-ttu-id="26e26-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="26e26-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26e26-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26e26-115">Attributes</span></span>

<span data-ttu-id="26e26-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="26e26-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="26e26-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26e26-117">Child elements</span></span>
  
|<span data-ttu-id="26e26-118">Element</span><span class="sxs-lookup"><span data-stu-id="26e26-118">Element</span></span>|<span data-ttu-id="26e26-119">Opis</span><span class="sxs-lookup"><span data-stu-id="26e26-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26e26-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="26e26-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="26e26-121">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="26e26-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="26e26-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26e26-122">Parent elements</span></span>  
  
|<span data-ttu-id="26e26-123">Element</span><span class="sxs-lookup"><span data-stu-id="26e26-123">Element</span></span>|<span data-ttu-id="26e26-124">Opis</span><span class="sxs-lookup"><span data-stu-id="26e26-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26e26-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="26e26-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="26e26-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="26e26-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26e26-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26e26-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="26e26-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="26e26-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="26e26-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="26e26-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
