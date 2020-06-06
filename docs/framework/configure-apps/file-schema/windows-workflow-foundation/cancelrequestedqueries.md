---
title: <cancelRequestedQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: eab5af7e-76fa-434d-9d36-873e995cee05
ms.openlocfilehash: 89297b3a7d64f4300a735d8512230d441836c634
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152310"
---
# \<cancelRequestedQueries>
<span data-ttu-id="690a0-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="690a0-101">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="690a0-102">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="690a0-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="690a0-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="690a0-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="690a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="690a0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="690a0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="690a0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="690a0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="690a0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="690a0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="690a0-107">Attributes</span></span>  
 <span data-ttu-id="690a0-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="690a0-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="690a0-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="690a0-109">Child Elements</span></span>  
  
|<span data-ttu-id="690a0-110">Element</span><span class="sxs-lookup"><span data-stu-id="690a0-110">Element</span></span>|<span data-ttu-id="690a0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="690a0-111">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](cancelrequestedquery.md)|<span data-ttu-id="690a0-112">Zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne</span><span class="sxs-lookup"><span data-stu-id="690a0-112">A query that is used to track requests to cancel a child activity by the parent activity</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="690a0-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="690a0-113">Parent Elements</span></span>  
  
|<span data-ttu-id="690a0-114">Element</span><span class="sxs-lookup"><span data-stu-id="690a0-114">Element</span></span>|<span data-ttu-id="690a0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="690a0-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="690a0-116">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="690a0-116">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="690a0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="690a0-117">See also</span></span>

- [<span data-ttu-id="690a0-118">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="690a0-118">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="690a0-119">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="690a0-119">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
