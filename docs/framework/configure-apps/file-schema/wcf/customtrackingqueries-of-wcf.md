---
title: <customTrackingQueries> w WCF
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 8b317cc289853902592e145e34b6e7bf5f84763b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282376"
---
# <a name="customtrackingqueries-of-wcf"></a><span data-ttu-id="ca069-102">\<customTrackingQueries > w WCF</span><span class="sxs-lookup"><span data-stu-id="ca069-102">\<customTrackingQueries> of WCF</span></span>

<span data-ttu-id="ca069-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ca069-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="ca069-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="ca069-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="ca069-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ca069-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="ca069-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ca069-106">\<system.serviceModel></span></span>  
<span data-ttu-id="ca069-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="ca069-107">\<tracking></span></span>  
<span data-ttu-id="ca069-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="ca069-108">\<profiles></span></span>  
<span data-ttu-id="ca069-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="ca069-109">\<trackingProfile></span></span>  
<span data-ttu-id="ca069-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ca069-110">\<workflow></span></span>  
<span data-ttu-id="ca069-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="ca069-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca069-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca069-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ca069-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ca069-113">Attributes and elements</span></span>

<span data-ttu-id="ca069-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ca069-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ca069-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ca069-115">Attributes</span></span>

<span data-ttu-id="ca069-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="ca069-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ca069-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ca069-117">Child elements</span></span>
  
|<span data-ttu-id="ca069-118">Element</span><span class="sxs-lookup"><span data-stu-id="ca069-118">Element</span></span>|<span data-ttu-id="ca069-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ca069-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca069-120">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="ca069-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="ca069-121">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="ca069-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ca069-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ca069-122">Parent elements</span></span>  
  
|<span data-ttu-id="ca069-123">Element</span><span class="sxs-lookup"><span data-stu-id="ca069-123">Element</span></span>|<span data-ttu-id="ca069-124">Opis</span><span class="sxs-lookup"><span data-stu-id="ca069-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ca069-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="ca069-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="ca069-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ca069-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ca069-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ca069-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ca069-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ca069-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ca069-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ca069-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
