---
title: <bookmarkResumptionQueries>programu WCF
ms.date: 03/30/2017
ms.assetid: ed086712-1dc7-4932-a592-d1116a0155f3
ms.openlocfilehash: 94ff9f44f295b45c03e1bd8f52a85d6b7b0c6e3b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850128"
---
# <a name="bookmarkresumptionqueries-of-wcf"></a><span data-ttu-id="966b9-102">\<bookmarkResumptionQueries>programu WCF</span><span class="sxs-lookup"><span data-stu-id="966b9-102">\<bookmarkResumptionQueries> of WCF</span></span>
  
<span data-ttu-id="966b9-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="966b9-103">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="966b9-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="966b9-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="966b9-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="966b9-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQueries>**  

## <a name="syntax"></a><span data-ttu-id="966b9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="966b9-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <bookmarkResumptionQueries>
          <bookmarkResumptionQuery name="String" />
        </bookmarkResumptionQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="966b9-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="966b9-107">Attributes and elements</span></span>  
  
<span data-ttu-id="966b9-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="966b9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="966b9-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="966b9-109">Attributes</span></span>  
  
<span data-ttu-id="966b9-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="966b9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="966b9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="966b9-111">Child elements</span></span>  
  
|<span data-ttu-id="966b9-112">Element</span><span class="sxs-lookup"><span data-stu-id="966b9-112">Element</span></span>|<span data-ttu-id="966b9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="966b9-113">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQuery>](bookmarkresumptionquery-of-wcf.md)|<span data-ttu-id="966b9-114">Zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="966b9-114">A query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="966b9-115">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="966b9-115">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="966b9-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="966b9-116">Parent elements</span></span>  
  
|<span data-ttu-id="966b9-117">Element</span><span class="sxs-lookup"><span data-stu-id="966b9-117">Element</span></span>|<span data-ttu-id="966b9-118">Opis</span><span class="sxs-lookup"><span data-stu-id="966b9-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="966b9-119">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="966b9-119">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="966b9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="966b9-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="966b9-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="966b9-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="966b9-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="966b9-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
