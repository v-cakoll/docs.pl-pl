---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: d49c6d933a09dce5d657746358f1a5f716ab639b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143367"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="acda6-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="acda6-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="acda6-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acda6-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="acda6-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="acda6-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="acda6-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="acda6-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="acda6-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="acda6-105">\<system.serviceModel></span></span>  
<span data-ttu-id="acda6-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="acda6-106">\<tracking></span></span>  
<span data-ttu-id="acda6-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="acda6-107">\<trackingProfile></span></span>  
<span data-ttu-id="acda6-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="acda6-108">\<workflow></span></span>  
<span data-ttu-id="acda6-109">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="acda6-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="acda6-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="acda6-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acda6-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="acda6-111">Syntax</span></span>  
  
```xml 
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String" 
                                childActivityName="String"/>
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acda6-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="acda6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="acda6-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acda6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acda6-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="acda6-114">Attributes</span></span>  
  
|<span data-ttu-id="acda6-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="acda6-115">Attribute</span></span>|<span data-ttu-id="acda6-116">Opis</span><span class="sxs-lookup"><span data-stu-id="acda6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acda6-117">activityName</span><span class="sxs-lookup"><span data-stu-id="acda6-117">activityName</span></span>|<span data-ttu-id="acda6-118">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="acda6-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="acda6-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="acda6-119">childActivityName</span></span>|<span data-ttu-id="acda6-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="acda6-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acda6-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="acda6-121">Child Elements</span></span>  
 <span data-ttu-id="acda6-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="acda6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acda6-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="acda6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="acda6-124">Element</span><span class="sxs-lookup"><span data-stu-id="acda6-124">Element</span></span>|<span data-ttu-id="acda6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="acda6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acda6-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="acda6-126">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="acda6-127">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acda6-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="acda6-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acda6-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="acda6-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="acda6-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="acda6-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="acda6-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
