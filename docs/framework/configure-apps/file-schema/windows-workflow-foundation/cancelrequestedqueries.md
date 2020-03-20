---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152310"
---
# <a name="cancelrequestedqueries"></a><span data-ttu-id="7b313-101">\<cancelRequestedQueries></span><span class="sxs-lookup"><span data-stu-id="7b313-101">\<cancelRequestedQueries></span></span>
<span data-ttu-id="7b313-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7b313-102">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="7b313-103">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="7b313-103">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="7b313-104">Aby uzyskać więcej informacji na temat śledzenia zapytań profilowych, zobacz [Śledzenie profili](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-104">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="7b313-105">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7b313-106">&nbsp;&nbsp;[**\<System.>z>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7b313-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>śledzenia**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="7b313-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="7b313-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7b313-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="7b313-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span><span class="sxs-lookup"><span data-stu-id="7b313-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b313-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b313-111">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <cancelRequestQueries>
        <cancelRequestQuery activityName="String"
                            childActivityName="String"/>
      </cancelRequestQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b313-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7b313-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7b313-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7b313-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b313-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7b313-114">Attributes</span></span>  
 <span data-ttu-id="7b313-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="7b313-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b313-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7b313-116">Child Elements</span></span>  
  
|<span data-ttu-id="7b313-117">Element</span><span class="sxs-lookup"><span data-stu-id="7b313-117">Element</span></span>|<span data-ttu-id="7b313-118">Opis</span><span class="sxs-lookup"><span data-stu-id="7b313-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b313-119">\<cancelRequestedQuery></span><span class="sxs-lookup"><span data-stu-id="7b313-119">\<cancelRequestedQuery></span></span>](cancelrequestedquery.md)|<span data-ttu-id="7b313-120">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b313-120">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b313-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7b313-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7b313-122">Element</span><span class="sxs-lookup"><span data-stu-id="7b313-122">Element</span></span>|<span data-ttu-id="7b313-123">Opis</span><span class="sxs-lookup"><span data-stu-id="7b313-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b313-124">\<>przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7b313-124">\<workflow></span></span>](workflow.md)|<span data-ttu-id="7b313-125">Element konfiguracji, który zawiera wszystkie kwerendy dla określonego przepływu pracy identyfikowane przez **activityDefinitionId** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b313-125">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b313-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b313-126">See also</span></span>

- [<span data-ttu-id="7b313-127">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7b313-127">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="7b313-128">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="7b313-128">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
