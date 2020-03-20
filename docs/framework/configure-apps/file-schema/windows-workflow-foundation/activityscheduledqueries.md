---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152427"
---
# <a name="activityscheduledqueries"></a><span data-ttu-id="9d1ec-101">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="9d1ec-101">\<activityScheduledQueries></span></span>
<span data-ttu-id="9d1ec-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-102">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="9d1ec-103">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-103">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="9d1ec-104">Aby uzyskać więcej informacji na temat śledzenia zapytań profilowych, zobacz [Śledzenie profili](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="9d1ec-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9d1ec-106">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="9d1ec-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="9d1ec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="9d1ec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="9d1ec-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="9d1ec-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span><span class="sxs-lookup"><span data-stu-id="9d1ec-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d1ec-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d1ec-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityScheduledQueries>
        <activityScheduledQuery activityName="String"
                                childActivityName="String" />
      </activityScheduledQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d1ec-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d1ec-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9d1ec-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d1ec-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d1ec-114">Attributes</span></span>  
 <span data-ttu-id="9d1ec-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d1ec-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d1ec-116">Child Elements</span></span>  
  
|<span data-ttu-id="9d1ec-117">Element</span><span class="sxs-lookup"><span data-stu-id="9d1ec-117">Element</span></span>|<span data-ttu-id="9d1ec-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9d1ec-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d1ec-119">\<działalnośćScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="9d1ec-119">\<activityScheduledQuery></span></span>](activityscheduledquery.md)|<span data-ttu-id="9d1ec-120">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-120">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d1ec-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d1ec-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d1ec-122">Element</span><span class="sxs-lookup"><span data-stu-id="9d1ec-122">Element</span></span>|<span data-ttu-id="9d1ec-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9d1ec-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d1ec-124">\<>przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9d1ec-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="9d1ec-125">Element konfiguracji, który zawiera wszystkie kwerendy dla określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="9d1ec-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d1ec-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d1ec-126">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="9d1ec-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9d1ec-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="9d1ec-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="9d1ec-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
