---
title: <activityScheduledQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850495"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="295c7-102">\<activityScheduledQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="295c7-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="295c7-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="295c7-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="295c7-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="295c7-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="295c7-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="295c7-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="295c7-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="295c7-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="295c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="295c7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="295c7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="295c7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="295c7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="295c7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityScheduledQueries >**</span><span class="sxs-lookup"><span data-stu-id="295c7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="295c7-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="295c7-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="295c7-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="295c7-114">Attributes and elements</span></span>  

<span data-ttu-id="295c7-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="295c7-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="295c7-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="295c7-116">Attributes</span></span>  

<span data-ttu-id="295c7-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="295c7-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="295c7-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="295c7-118">Child elements</span></span>  
  
|<span data-ttu-id="295c7-119">Element</span><span class="sxs-lookup"><span data-stu-id="295c7-119">Element</span></span>|<span data-ttu-id="295c7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="295c7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="295c7-121">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="295c7-121">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="295c7-122">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="295c7-122">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="295c7-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="295c7-123">Parent elements</span></span>  
  
|<span data-ttu-id="295c7-124">Element</span><span class="sxs-lookup"><span data-stu-id="295c7-124">Element</span></span>|<span data-ttu-id="295c7-125">Opis</span><span class="sxs-lookup"><span data-stu-id="295c7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="295c7-126">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="295c7-126">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="295c7-127">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="295c7-127">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="295c7-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="295c7-128">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="295c7-129">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="295c7-129">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="295c7-130">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="295c7-130">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
