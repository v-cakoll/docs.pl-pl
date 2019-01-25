---
title: '&lt;customTrackingQueries&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4e9e732d-911d-45a3-a569-4b5e9cd1ffbe
ms.openlocfilehash: 757bbe500ec3edccef465b7ff23b2c974e4a5011
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598844"
---
# <a name="ltcustomtrackingqueriesgt"></a><span data-ttu-id="e732e-102">&lt;customTrackingQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="e732e-102">&lt;customTrackingQueries&gt;</span></span>
<span data-ttu-id="e732e-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="e732e-103">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="e732e-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania śledzenia niestandardowe rekordów.</span><span class="sxs-lookup"><span data-stu-id="e732e-104">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>  
  
 <span data-ttu-id="e732e-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e732e-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e732e-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e732e-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e732e-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e732e-107">\<tracking></span></span>  
<span data-ttu-id="e732e-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e732e-108">\<trackingProfile></span></span>  
<span data-ttu-id="e732e-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e732e-109">\<workflow></span></span>  
<span data-ttu-id="e732e-110">\<customTrackingQueries></span><span class="sxs-lookup"><span data-stu-id="e732e-110">\<customTrackingQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e732e-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e732e-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e732e-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e732e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e732e-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e732e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e732e-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e732e-114">Attributes</span></span>  
 <span data-ttu-id="e732e-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="e732e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e732e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e732e-116">Child Elements</span></span>  
  
|<span data-ttu-id="e732e-117">Element</span><span class="sxs-lookup"><span data-stu-id="e732e-117">Element</span></span>|<span data-ttu-id="e732e-118">Opis</span><span class="sxs-lookup"><span data-stu-id="e732e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e732e-119">\<customTrackingQuery></span><span class="sxs-lookup"><span data-stu-id="e732e-119">\<customTrackingQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/customtrackingquery.md)|<span data-ttu-id="e732e-120">Zapytanie, które jest używane do śledzenia zdarzeń zdefiniowanych przez użytkownika w działaniach kodu.</span><span class="sxs-lookup"><span data-stu-id="e732e-120">A query that is used to track events that you define in your code activities.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e732e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e732e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e732e-122">Element</span><span class="sxs-lookup"><span data-stu-id="e732e-122">Element</span></span>|<span data-ttu-id="e732e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e732e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e732e-124">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e732e-124">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="e732e-125">Element konfiguracji, który zawiera wszystkie zapytania dotyczące określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e732e-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e732e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e732e-126">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e732e-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e732e-127">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e732e-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e732e-128">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
