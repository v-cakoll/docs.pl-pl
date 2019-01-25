---
title: '&lt;activityScheduledQuery&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: a8bcd6d4-b389-4daf-86bf-1ade85fec114
ms.openlocfilehash: 0e69c32a7c292fda90828396c402c95e4899600a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687443"
---
# <a name="ltactivityscheduledquerygt"></a><span data-ttu-id="e227c-102">&lt;activityScheduledQuery&gt;</span><span class="sxs-lookup"><span data-stu-id="e227c-102">&lt;activityScheduledQuery&gt;</span></span>
<span data-ttu-id="e227c-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e227c-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="e227c-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="e227c-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="e227c-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="e227c-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="e227c-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e227c-106">\<system.serviceModel></span></span>  
<span data-ttu-id="e227c-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="e227c-107">\<tracking></span></span>  
<span data-ttu-id="e227c-108">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="e227c-108">\<trackingProfile></span></span>  
<span data-ttu-id="e227c-109">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="e227c-109">\<workflow></span></span>  
<span data-ttu-id="e227c-110">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="e227c-110">\<activityScheduledQueries></span></span>  
<span data-ttu-id="e227c-111">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e227c-111">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e227c-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e227c-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e227c-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e227c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e227c-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e227c-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e227c-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e227c-115">Attributes</span></span>  
  
|<span data-ttu-id="e227c-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e227c-116">Attribute</span></span>|<span data-ttu-id="e227c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e227c-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e227c-118">activityName</span><span class="sxs-lookup"><span data-stu-id="e227c-118">activityName</span></span>|<span data-ttu-id="e227c-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="e227c-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="e227c-120">childActivityName</span><span class="sxs-lookup"><span data-stu-id="e227c-120">childActivityName</span></span>|<span data-ttu-id="e227c-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="e227c-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e227c-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e227c-122">Child Elements</span></span>  
 <span data-ttu-id="e227c-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e227c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e227c-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e227c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e227c-125">Element</span><span class="sxs-lookup"><span data-stu-id="e227c-125">Element</span></span>|<span data-ttu-id="e227c-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e227c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e227c-127">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="e227c-127">\<activityScheduledQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activityscheduledquery.md)|<span data-ttu-id="e227c-128">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e227c-128">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e227c-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e227c-129">See also</span></span>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="e227c-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e227c-130">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="e227c-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="e227c-131">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
