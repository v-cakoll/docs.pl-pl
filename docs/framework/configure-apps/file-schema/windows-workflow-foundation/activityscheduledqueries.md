---
title: <activityScheduledQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ca6e82f1-54f2-48d6-899c-9873065b5547
ms.openlocfilehash: 763754b95a7f39c7f35e05df28589b69352168e6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152427"
---
# \<activityScheduledQueries>
<span data-ttu-id="ee82f-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee82f-101">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="ee82f-102">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="ee82f-102">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
 <span data-ttu-id="ee82f-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="ee82f-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="ee82f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee82f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee82f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ee82f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ee82f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee82f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee82f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ee82f-107">Attributes</span></span>  
 <span data-ttu-id="ee82f-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee82f-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ee82f-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ee82f-109">Child Elements</span></span>  
  
|<span data-ttu-id="ee82f-110">Element</span><span class="sxs-lookup"><span data-stu-id="ee82f-110">Element</span></span>|<span data-ttu-id="ee82f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ee82f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQuery>](activityscheduledquery.md)|<span data-ttu-id="ee82f-112">Zapytanie, które jest używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ee82f-112">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ee82f-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ee82f-113">Parent Elements</span></span>  
  
|<span data-ttu-id="ee82f-114">Element</span><span class="sxs-lookup"><span data-stu-id="ee82f-114">Element</span></span>|<span data-ttu-id="ee82f-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ee82f-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="ee82f-116">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ee82f-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ee82f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee82f-117">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityScheduledQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ee82f-118">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ee82f-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ee82f-119">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ee82f-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
