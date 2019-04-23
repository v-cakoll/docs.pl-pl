---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120084"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="dd1af-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="dd1af-101">\<customTrackingQueries></span></span>
<span data-ttu-id="dd1af-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="dd1af-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="dd1af-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="dd1af-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="dd1af-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="dd1af-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="dd1af-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="dd1af-105">\<system.serviceModel></span></span>  
<span data-ttu-id="dd1af-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="dd1af-106">\<tracking></span></span>  
<span data-ttu-id="dd1af-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dd1af-107">\<trackingProfile></span></span>  
<span data-ttu-id="dd1af-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="dd1af-108">\<workflow></span></span>  
<span data-ttu-id="dd1af-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="dd1af-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd1af-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd1af-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd1af-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd1af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="dd1af-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dd1af-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd1af-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd1af-113">Attributes</span></span>  
 <span data-ttu-id="dd1af-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="dd1af-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd1af-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd1af-115">Child Elements</span></span>  
  
|<span data-ttu-id="dd1af-116">Element</span><span class="sxs-lookup"><span data-stu-id="dd1af-116">Element</span></span>|<span data-ttu-id="dd1af-117">Opis</span><span class="sxs-lookup"><span data-stu-id="dd1af-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd1af-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="dd1af-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="dd1af-119">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="dd1af-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd1af-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd1af-120">Parent Elements</span></span>  
  
|<span data-ttu-id="dd1af-121">Element</span><span class="sxs-lookup"><span data-stu-id="dd1af-121">Element</span></span>|<span data-ttu-id="dd1af-122">Opis</span><span class="sxs-lookup"><span data-stu-id="dd1af-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd1af-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="dd1af-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="dd1af-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="dd1af-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd1af-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd1af-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="dd1af-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="dd1af-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dd1af-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="dd1af-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
