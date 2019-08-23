---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 429940b2ed69d8be497626f634a21adca540b529
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945832"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="de719-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="de719-101">\<customTrackingQueries></span></span>
<span data-ttu-id="de719-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="de719-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="de719-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="de719-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="de719-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="de719-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="de719-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="de719-105">\<system.serviceModel></span></span>  
<span data-ttu-id="de719-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="de719-106">\<tracking></span></span>  
<span data-ttu-id="de719-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="de719-107">\<trackingProfile></span></span>  
<span data-ttu-id="de719-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="de719-108">\<workflow></span></span>  
<span data-ttu-id="de719-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="de719-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de719-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="de719-110">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <customTrackingQueries>
        <customTrackingQuery activityName="String" 
                             name="String" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de719-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="de719-111">Attributes and Elements</span></span>  
 <span data-ttu-id="de719-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="de719-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de719-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="de719-113">Attributes</span></span>  
 <span data-ttu-id="de719-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="de719-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="de719-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="de719-115">Child Elements</span></span>  
  
|<span data-ttu-id="de719-116">Element</span><span class="sxs-lookup"><span data-stu-id="de719-116">Element</span></span>|<span data-ttu-id="de719-117">Opis</span><span class="sxs-lookup"><span data-stu-id="de719-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de719-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="de719-118">\<customTrackingQuery></span></span>](customtrackingquery.md)|<span data-ttu-id="de719-119">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="de719-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de719-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="de719-120">Parent Elements</span></span>  
  
|<span data-ttu-id="de719-121">Element</span><span class="sxs-lookup"><span data-stu-id="de719-121">Element</span></span>|<span data-ttu-id="de719-122">Opis</span><span class="sxs-lookup"><span data-stu-id="de719-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de719-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="de719-123">\<workflow></span></span>](workflow.md)|<span data-ttu-id="de719-124">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="de719-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de719-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de719-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="de719-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="de719-126">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="de719-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="de719-127">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
