---
title: <activityScheduledQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: dc04405204be7c5484d47b4a3767f846b11abf9f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945501"
---
# <a name="activityscheduledquery"></a><span data-ttu-id="3e42a-101">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="3e42a-101">\<activityScheduledQuery></span></span>
<span data-ttu-id="3e42a-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e42a-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="3e42a-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="3e42a-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="3e42a-104">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="3e42a-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="3e42a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3e42a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3e42a-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="3e42a-106">\<tracking></span></span>  
<span data-ttu-id="3e42a-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="3e42a-107">\<trackingProfile></span></span>  
<span data-ttu-id="3e42a-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="3e42a-108">\<workflow></span></span>  
<span data-ttu-id="3e42a-109">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="3e42a-109">\<activityScheduledQueries></span></span>  
<span data-ttu-id="3e42a-110">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="3e42a-110">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e42a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e42a-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e42a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e42a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3e42a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e42a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e42a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e42a-114">Attributes</span></span>  
  
|<span data-ttu-id="3e42a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e42a-115">Attribute</span></span>|<span data-ttu-id="3e42a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3e42a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e42a-117">activityName</span><span class="sxs-lookup"><span data-stu-id="3e42a-117">activityName</span></span>|<span data-ttu-id="3e42a-118">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="3e42a-118">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="3e42a-119">childActivityName</span><span class="sxs-lookup"><span data-stu-id="3e42a-119">childActivityName</span></span>|<span data-ttu-id="3e42a-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="3e42a-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e42a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e42a-121">Child Elements</span></span>  
 <span data-ttu-id="3e42a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="3e42a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e42a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e42a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3e42a-124">Element</span><span class="sxs-lookup"><span data-stu-id="3e42a-124">Element</span></span>|<span data-ttu-id="3e42a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="3e42a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e42a-126">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="3e42a-126">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="3e42a-127">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e42a-127">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3e42a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e42a-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="3e42a-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3e42a-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="3e42a-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="3e42a-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
