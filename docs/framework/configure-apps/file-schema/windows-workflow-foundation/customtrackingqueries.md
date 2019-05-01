---
title: <customTrackingQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 663dda571990a86dc71ea927c4e97241e0ed3fc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790224"
---
# <a name="customtrackingqueries"></a><span data-ttu-id="8c61d-101">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="8c61d-101">\<customTrackingQueries></span></span>
<span data-ttu-id="8c61d-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="8c61d-102">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="8c61d-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="8c61d-103">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="8c61d-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="8c61d-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="8c61d-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8c61d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="8c61d-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="8c61d-106">\<tracking></span></span>  
<span data-ttu-id="8c61d-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="8c61d-107">\<trackingProfile></span></span>  
<span data-ttu-id="8c61d-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8c61d-108">\<workflow></span></span>  
<span data-ttu-id="8c61d-109">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="8c61d-109">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c61d-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c61d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c61d-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8c61d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8c61d-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8c61d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c61d-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8c61d-113">Attributes</span></span>  
 <span data-ttu-id="8c61d-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="8c61d-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8c61d-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c61d-115">Child Elements</span></span>  
  
|<span data-ttu-id="8c61d-116">Element</span><span class="sxs-lookup"><span data-stu-id="8c61d-116">Element</span></span>|<span data-ttu-id="8c61d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="8c61d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c61d-118">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="8c61d-118">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="8c61d-119">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="8c61d-119">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c61d-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c61d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8c61d-121">Element</span><span class="sxs-lookup"><span data-stu-id="8c61d-121">Element</span></span>|<span data-ttu-id="8c61d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8c61d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c61d-123">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="8c61d-123">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="8c61d-124">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c61d-124">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8c61d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c61d-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8c61d-126">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8c61d-126">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8c61d-127">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8c61d-127">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
