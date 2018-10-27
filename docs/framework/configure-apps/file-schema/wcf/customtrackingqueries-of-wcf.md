---
title: '&lt;customTrackingQueries&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 060e2b5c8efd51f6245a39bd9562a69f0111fd41
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50038789"
---
# <a name="ltcustomtrackingqueriesgt-of-wcf"></a><span data-ttu-id="eb072-102">&lt;customTrackingQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="eb072-102">&lt;customTrackingQueries&gt; of WCF</span></span>

<span data-ttu-id="eb072-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="eb072-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="eb072-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="eb072-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="eb072-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="eb072-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>
  
<span data-ttu-id="eb072-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb072-106">\<system.serviceModel></span></span>  
<span data-ttu-id="eb072-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="eb072-107">\<tracking></span></span>  
<span data-ttu-id="eb072-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="eb072-108">\<profiles></span></span>  
<span data-ttu-id="eb072-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eb072-109">\<trackingProfile></span></span>  
<span data-ttu-id="eb072-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="eb072-110">\<workflow></span></span>  
<span data-ttu-id="eb072-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="eb072-111">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb072-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb072-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb072-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb072-113">Attributes and elements</span></span>

<span data-ttu-id="eb072-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb072-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb072-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb072-115">Attributes</span></span>

<span data-ttu-id="eb072-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb072-116">None.</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="eb072-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb072-117">Child elements</span></span>
  
|<span data-ttu-id="eb072-118">Element</span><span class="sxs-lookup"><span data-stu-id="eb072-118">Element</span></span>|<span data-ttu-id="eb072-119">Opis</span><span class="sxs-lookup"><span data-stu-id="eb072-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb072-120">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="eb072-120">\<customTrackingQuery></span></span>](customtrackingquery-of-wcf.md)|<span data-ttu-id="eb072-121">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="eb072-121">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb072-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb072-122">Parent elements</span></span>  
  
|<span data-ttu-id="eb072-123">Element</span><span class="sxs-lookup"><span data-stu-id="eb072-123">Element</span></span>|<span data-ttu-id="eb072-124">Opis</span><span class="sxs-lookup"><span data-stu-id="eb072-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb072-125">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="eb072-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="eb072-126">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb072-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb072-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb072-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>       
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>       
- [<span data-ttu-id="eb072-128">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="eb072-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="eb072-129">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="eb072-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
