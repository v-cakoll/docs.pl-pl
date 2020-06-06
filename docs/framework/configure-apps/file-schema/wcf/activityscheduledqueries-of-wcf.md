---
title: <activityScheduledQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: c2281a9027aabfc5255ef7b09176f60d1725b522
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850495"
---
# <a name="activityscheduledqueries-of-wcf"></a><span data-ttu-id="b792f-102">\<activityScheduledQueries>programu WCF</span><span class="sxs-lookup"><span data-stu-id="b792f-102">\<activityScheduledQueries> of WCF</span></span>
<span data-ttu-id="b792f-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b792f-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="b792f-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="b792f-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="b792f-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="b792f-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="b792f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b792f-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b792f-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b792f-107">Attributes and elements</span></span>  

<span data-ttu-id="b792f-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b792f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b792f-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b792f-109">Attributes</span></span>  

<span data-ttu-id="b792f-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="b792f-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b792f-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b792f-111">Child elements</span></span>  
  
|<span data-ttu-id="b792f-112">Element</span><span class="sxs-lookup"><span data-stu-id="b792f-112">Element</span></span>|<span data-ttu-id="b792f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b792f-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="b792f-114">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b792f-114">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b792f-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b792f-115">Parent elements</span></span>  
  
|<span data-ttu-id="b792f-116">Element</span><span class="sxs-lookup"><span data-stu-id="b792f-116">Element</span></span>|<span data-ttu-id="b792f-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b792f-117">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="b792f-118">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="b792f-118">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b792f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b792f-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="b792f-120">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b792f-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="b792f-121">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="b792f-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
