---
title: <activityScheduledQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: b173964cf5d691f4b9300bca69ca4a1fe1ea7e11
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850468"
---
# <a name="activityscheduledquery-of-wcf"></a><span data-ttu-id="c2fb9-102">\<activityScheduledQuery>programu WCF</span><span class="sxs-lookup"><span data-stu-id="c2fb9-102">\<activityScheduledQuery> of WCF</span></span>

<span data-ttu-id="c2fb9-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia działania zaPLanowane do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="c2fb9-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zaPLanowane rekordów.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="c2fb9-105">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="c2fb9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityScheduledQueries>**](activityscheduledqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityScheduledQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="c2fb9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2fb9-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2fb9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2fb9-107">Attributes and elements</span></span>  

<span data-ttu-id="c2fb9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2fb9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2fb9-109">Attributes</span></span>  
  
|<span data-ttu-id="c2fb9-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2fb9-110">Attribute</span></span>|<span data-ttu-id="c2fb9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c2fb9-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="c2fb9-112">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="c2fb9-113">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2fb9-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2fb9-114">Child elements</span></span>

<span data-ttu-id="c2fb9-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c2fb9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2fb9-116">Parent elements</span></span>  
  
|<span data-ttu-id="c2fb9-117">Element</span><span class="sxs-lookup"><span data-stu-id="c2fb9-117">Element</span></span>|<span data-ttu-id="c2fb9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="c2fb9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|<span data-ttu-id="c2fb9-119">Kolekcja zapytań, które są używane do śledzenia działania zaplanowanego do wykonania przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2fb9-119">A collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2fb9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2fb9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="c2fb9-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c2fb9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="c2fb9-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="c2fb9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
