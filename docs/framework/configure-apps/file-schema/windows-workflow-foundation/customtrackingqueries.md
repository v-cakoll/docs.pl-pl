---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120084"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="9286e-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9286e-101">\<customTrackingQueries></span></span>
<span data-ttu-id="9286e-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="9286e-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="9286e-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="9286e-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="9286e-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9286e-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9286e-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9286e-105">\<system.serviceModel></span></span>  
<span data-ttu-id="9286e-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="9286e-106">\<tracking></span></span>  
<span data-ttu-id="9286e-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="9286e-107">\<trackingProfile></span></span>  
<span data-ttu-id="9286e-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9286e-108">\<workflow></span></span>  
<span data-ttu-id="9286e-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="9286e-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9286e-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="9286e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9286e-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9286e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9286e-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9286e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9286e-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9286e-113">Attributes</span></span>  
 <span data-ttu-id="9286e-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="9286e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9286e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9286e-115">Child Elements</span></span>  
  
|<span data-ttu-id="9286e-116">Element</span><span class="sxs-lookup"><span data-stu-id="9286e-116">Element</span></span>|<span data-ttu-id="9286e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="9286e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9286e-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="9286e-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="9286e-119">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="9286e-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9286e-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9286e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9286e-121">Element</span><span class="sxs-lookup"><span data-stu-id="9286e-121">Element</span></span>|<span data-ttu-id="9286e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="9286e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9286e-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="9286e-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="9286e-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9286e-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9286e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9286e-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9286e-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9286e-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9286e-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9286e-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
