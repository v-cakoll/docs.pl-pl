---
title: '&lt;customTrackingQuery&gt; w WCF'
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: e13064afbd9f5dbc8d7216eb384001e1e005785c
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316236"
---
# <a name="ltcustomtrackingquerygt-of-wcf"></a><span data-ttu-id="aa816-102">&lt;customTrackingQuery&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="aa816-102">&lt;customTrackingQuery&gt; of WCF</span></span>

<span data-ttu-id="aa816-103">Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="aa816-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="aa816-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="aa816-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="aa816-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="aa816-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="aa816-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="aa816-106">\<system.serviceModel></span></span>  
<span data-ttu-id="aa816-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="aa816-107">\<tracking></span></span>  
<span data-ttu-id="aa816-108">\<profile ></span><span class="sxs-lookup"><span data-stu-id="aa816-108">\<profiles></span></span>  
<span data-ttu-id="aa816-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="aa816-109">\<trackingProfile></span></span>  
<span data-ttu-id="aa816-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="aa816-110">\<workflow></span></span>  
<span data-ttu-id="aa816-111">\<customTrackingQueries ></span><span class="sxs-lookup"><span data-stu-id="aa816-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="aa816-112">\<customTrackingQuery ></span><span class="sxs-lookup"><span data-stu-id="aa816-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa816-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa816-113">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="aa816-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aa816-114">Attributes and elements</span></span>  

<span data-ttu-id="aa816-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aa816-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa816-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aa816-116">Attributes</span></span>  
  
|<span data-ttu-id="aa816-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aa816-117">Attribute</span></span>|<span data-ttu-id="aa816-118">Opis</span><span class="sxs-lookup"><span data-stu-id="aa816-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="aa816-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="aa816-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="aa816-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="aa816-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa816-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aa816-121">Child elements</span></span>

<span data-ttu-id="aa816-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="aa816-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="aa816-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aa816-123">Parent elements</span></span>

|<span data-ttu-id="aa816-124">Element</span><span class="sxs-lookup"><span data-stu-id="aa816-124">Element</span></span>|<span data-ttu-id="aa816-125">Opis</span><span class="sxs-lookup"><span data-stu-id="aa816-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa816-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="aa816-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="aa816-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="aa816-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="aa816-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa816-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="aa816-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="aa816-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="aa816-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="aa816-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
