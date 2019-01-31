---
title: <activityScheduledQuery> w WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 5087d56092296f8c68b719ec0945993adeb3de0a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272906"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="19b15-102">\<activityScheduledQuery > w WCF</span><span class="sxs-lookup"><span data-stu-id="19b15-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="19b15-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19b15-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="19b15-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="19b15-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="19b15-105">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="19b15-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="19b15-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="19b15-106">\<system.serviceModel></span></span>  
<span data-ttu-id="19b15-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="19b15-107">\<tracking></span></span>  
<span data-ttu-id="19b15-108">\<profiles></span><span class="sxs-lookup"><span data-stu-id="19b15-108">\<profiles></span></span>  
<span data-ttu-id="19b15-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="19b15-109">\<trackingProfile></span></span>  
<span data-ttu-id="19b15-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="19b15-110">\<workflow></span></span>  
<span data-ttu-id="19b15-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="19b15-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="19b15-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="19b15-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19b15-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="19b15-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19b15-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="19b15-114">Attributes and elements</span></span>  

<span data-ttu-id="19b15-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19b15-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19b15-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="19b15-116">Attributes</span></span>  
  
|<span data-ttu-id="19b15-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="19b15-117">Attribute</span></span>|<span data-ttu-id="19b15-118">Opis</span><span class="sxs-lookup"><span data-stu-id="19b15-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="19b15-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="19b15-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="19b15-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="19b15-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19b15-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="19b15-121">Child elements</span></span>

<span data-ttu-id="19b15-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="19b15-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="19b15-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="19b15-123">Parent elements</span></span>  
  
|<span data-ttu-id="19b15-124">Element</span><span class="sxs-lookup"><span data-stu-id="19b15-124">Element</span></span>|<span data-ttu-id="19b15-125">Opis</span><span class="sxs-lookup"><span data-stu-id="19b15-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19b15-126">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="19b15-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="19b15-127">Kolekcję zapytań, które są używane do śledzenia działania zaplanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="19b15-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19b15-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19b15-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="19b15-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="19b15-129">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="19b15-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="19b15-130">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
