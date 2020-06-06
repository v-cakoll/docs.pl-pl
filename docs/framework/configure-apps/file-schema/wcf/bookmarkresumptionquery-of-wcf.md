---
title: <bookmarkResumptionQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: 755a34f0-87c9-4a1e-ae4d-0fb8a6fbdc0e
ms.openlocfilehash: 8cb254599a9742305ec958fd77174f4c4b8a57c2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834002"
---
# <a name="bookmarkresumptionquery-of-wcf"></a><span data-ttu-id="d3ad6-102">\<bookmarkResumptionQuery>programu WCF</span><span class="sxs-lookup"><span data-stu-id="d3ad6-102">\<bookmarkResumptionQuery> of WCF</span></span>

<span data-ttu-id="d3ad6-103">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-103">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="d3ad6-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-104">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
<span data-ttu-id="d3ad6-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d3ad6-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="d3ad6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3ad6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3ad6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d3ad6-107">Attributes and elements</span></span>

<span data-ttu-id="d3ad6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3ad6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d3ad6-109">Attributes</span></span>  
  
|<span data-ttu-id="d3ad6-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d3ad6-110">Attribute</span></span>|<span data-ttu-id="d3ad6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d3ad6-111">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d3ad6-112">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-112">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3ad6-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d3ad6-113">Child elements</span></span>

<span data-ttu-id="d3ad6-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-114">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="d3ad6-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d3ad6-115">Parent elements</span></span>  
  
|<span data-ttu-id="d3ad6-116">Element</span><span class="sxs-lookup"><span data-stu-id="d3ad6-116">Element</span></span>|<span data-ttu-id="d3ad6-117">Opis</span><span class="sxs-lookup"><span data-stu-id="d3ad6-117">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries-of-wcf.md)|<span data-ttu-id="d3ad6-118">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d3ad6-118">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3ad6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d3ad6-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="d3ad6-120">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d3ad6-120">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d3ad6-121">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d3ad6-121">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
