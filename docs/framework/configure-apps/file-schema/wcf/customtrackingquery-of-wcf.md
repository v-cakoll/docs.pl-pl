---
title: <customTrackingQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 164446ae-8440-4b67-b217-6786cfae1e01
ms.openlocfilehash: b034727dc89b58794ec2834cb0ff39cd7e5f1dca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919361"
---
# <a name="customtrackingquery-of-wcf"></a><span data-ttu-id="d6ffa-102">\<customTrackingQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="d6ffa-102">\<customTrackingQuery> of WCF</span></span>

<span data-ttu-id="d6ffa-103">Reprezentuje zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-103">Represents a query that is used to track events that you define in your code activities.</span></span> <span data-ttu-id="d6ffa-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>

<span data-ttu-id="d6ffa-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="d6ffa-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="d6ffa-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d6ffa-106">\<system.serviceModel></span></span>  
<span data-ttu-id="d6ffa-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="d6ffa-107">\<tracking></span></span>  
<span data-ttu-id="d6ffa-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="d6ffa-108">\<profiles></span></span>  
<span data-ttu-id="d6ffa-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="d6ffa-109">\<trackingProfile></span></span>  
<span data-ttu-id="d6ffa-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="d6ffa-110">\<workflow></span></span>  
<span data-ttu-id="d6ffa-111">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d6ffa-111">\<customTrackingQueries></span></span>  
<span data-ttu-id="d6ffa-112">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="d6ffa-112">\<customTrackingQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ffa-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6ffa-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6ffa-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d6ffa-114">Attributes and elements</span></span>  

<span data-ttu-id="d6ffa-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6ffa-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d6ffa-116">Attributes</span></span>  
  
|<span data-ttu-id="d6ffa-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d6ffa-117">Attribute</span></span>|<span data-ttu-id="d6ffa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d6ffa-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="d6ffa-119">Ciąg określający nazwę działania, który wygenerował rekord śledzenia.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-119">A string that specifies the name of the activity that generated the tracking record.</span></span>|  
|`name`|<span data-ttu-id="d6ffa-120">Ciąg, który określa nazwę rekord śledzenia niestandardowego, który jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-120">A string that specifies the name of the custom tracking record that is emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6ffa-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d6ffa-121">Child elements</span></span>

<span data-ttu-id="d6ffa-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d6ffa-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d6ffa-123">Parent elements</span></span>

|<span data-ttu-id="d6ffa-124">Element</span><span class="sxs-lookup"><span data-stu-id="d6ffa-124">Element</span></span>|<span data-ttu-id="d6ffa-125">Opis</span><span class="sxs-lookup"><span data-stu-id="d6ffa-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6ffa-126">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="d6ffa-126">\<customTrackingQueries></span></span>](customtrackingqueries-of-wcf.md)|<span data-ttu-id="d6ffa-127">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="d6ffa-127">Represents a collection of queries that are used to track events that you define in your code activities.</span></span>|
  
## <a name="see-also"></a><span data-ttu-id="d6ffa-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6ffa-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d6ffa-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d6ffa-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d6ffa-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d6ffa-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
