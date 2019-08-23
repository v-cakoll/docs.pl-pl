---
title: <activityScheduledQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: 7787ada68210ff832ff3fd1ec93c9d346e4d2eaa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926926"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="81de4-102">\<activityScheduledQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="81de4-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="81de4-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81de4-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="81de4-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="81de4-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="81de4-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="81de4-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="81de4-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="81de4-106">\<system.serviceModel></span></span>  
<span data-ttu-id="81de4-107">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="81de4-107">\<tracking></span></span>  
<span data-ttu-id="81de4-108">\<> profilów</span><span class="sxs-lookup"><span data-stu-id="81de4-108">\<profiles></span></span>  
<span data-ttu-id="81de4-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="81de4-109">\<trackingProfile></span></span>  
<span data-ttu-id="81de4-110">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="81de4-110">\<workflow></span></span>  
<span data-ttu-id="81de4-111">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="81de4-111">\<activityScheduledQueries></span></span>  
<span data-ttu-id="81de4-112">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="81de4-112">\<activityScheduledQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81de4-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="81de4-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81de4-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="81de4-114">Attributes and elements</span></span>  

<span data-ttu-id="81de4-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81de4-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81de4-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="81de4-116">Attributes</span></span>  
  
|<span data-ttu-id="81de4-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="81de4-117">Attribute</span></span>|<span data-ttu-id="81de4-118">Opis</span><span class="sxs-lookup"><span data-stu-id="81de4-118">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="81de4-119">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="81de4-119">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="81de4-120">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="81de4-120">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81de4-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="81de4-121">Child elements</span></span>

<span data-ttu-id="81de4-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="81de4-122">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="81de4-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="81de4-123">Parent elements</span></span>  
  
|<span data-ttu-id="81de4-124">Element</span><span class="sxs-lookup"><span data-stu-id="81de4-124">Element</span></span>|<span data-ttu-id="81de4-125">Opis</span><span class="sxs-lookup"><span data-stu-id="81de4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81de4-126">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="81de4-126">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="81de4-127">Kolekcja zapytań, które są używane do śledzenia działania zaplanowanego do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81de4-127">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81de4-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81de4-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="81de4-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="81de4-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="81de4-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="81de4-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
