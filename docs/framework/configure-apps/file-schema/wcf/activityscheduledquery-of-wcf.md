---
title: <activityScheduledQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850468"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="ce251-102">\<activityScheduledQuery > WCF</span><span class="sxs-lookup"><span data-stu-id="ce251-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="ce251-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce251-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ce251-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="ce251-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="ce251-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="ce251-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ce251-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ce251-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="ce251-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="ce251-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="ce251-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="ce251-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="ce251-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<activityScheduledQueries >** ](activityscheduledqueries-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="ce251-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)</span></span>\
<span data-ttu-id="ce251-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQuery >**</span><span class="sxs-lookup"><span data-stu-id="ce251-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce251-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce251-114">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce251-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ce251-115">Attributes and elements</span></span>  

<span data-ttu-id="ce251-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce251-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce251-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ce251-117">Attributes</span></span>  
  
|<span data-ttu-id="ce251-118">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ce251-118">Attribute</span></span>|<span data-ttu-id="ce251-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ce251-119">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="ce251-120">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="ce251-120">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="ce251-121">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="ce251-121">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce251-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ce251-122">Child elements</span></span>

<span data-ttu-id="ce251-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="ce251-123">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="ce251-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ce251-124">Parent elements</span></span>  
  
|<span data-ttu-id="ce251-125">Element</span><span class="sxs-lookup"><span data-stu-id="ce251-125">Element</span></span>|<span data-ttu-id="ce251-126">Opis</span><span class="sxs-lookup"><span data-stu-id="ce251-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce251-127">\<activityScheduledQueries ></span><span class="sxs-lookup"><span data-stu-id="ce251-127">\<activityScheduledQueries></span></span>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="ce251-128">Kolekcja zapytań, które są używane do śledzenia działania zaplanowanego do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ce251-128">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce251-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce251-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="ce251-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ce251-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ce251-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ce251-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
