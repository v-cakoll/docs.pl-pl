---
title: <bookmarkResumptionQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8ed61a7f-4254-439c-bdd8-b474971533f7
ms.openlocfilehash: 563e0cbd3f50887e1c9e3d47a3c9502acc13b2c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398868"
---
# \<bookmarkResumptionQueries>
<span data-ttu-id="bf301-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf301-101">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bf301-102">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="bf301-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="bf301-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="bf301-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="bf301-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf301-104">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <bookmarkResumptionQueries>
        <bookmarkResumptionQuery name="String" />
      </bookmarkResumptionQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf301-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf301-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bf301-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf301-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf301-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf301-107">Attributes</span></span>  
 <span data-ttu-id="bf301-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="bf301-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bf301-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf301-109">Child Elements</span></span>  
  
|<span data-ttu-id="bf301-110">Element</span><span class="sxs-lookup"><span data-stu-id="bf301-110">Element</span></span>|<span data-ttu-id="bf301-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bf301-111">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery.md)|<span data-ttu-id="bf301-112">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf301-112">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="bf301-113">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="bf301-113">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf301-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf301-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bf301-115">Element</span><span class="sxs-lookup"><span data-stu-id="bf301-115">Element</span></span>|<span data-ttu-id="bf301-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bf301-116">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="bf301-117">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="bf301-117">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf301-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf301-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="bf301-119">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bf301-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="bf301-120">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="bf301-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
