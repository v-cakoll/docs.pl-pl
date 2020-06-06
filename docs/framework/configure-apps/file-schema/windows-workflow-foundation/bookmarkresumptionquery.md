---
title: <bookmarkResumptionQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 226de75d-d25c-48d5-b069-4b7d80a6852b
ms.openlocfilehash: b2a81a42a17474bdb0124bec6d3c3eeefa514411
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398848"
---
# \<bookmarkResumptionQuery>
<span data-ttu-id="794d0-101">Reprezentuje zapytanie, które jest używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="794d0-101">Represents a query that is used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="794d0-102">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania zakładki wznowienie rekordów.</span><span class="sxs-lookup"><span data-stu-id="794d0-102">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>  
  
 <span data-ttu-id="794d0-103">Aby uzyskać więcej informacji o śledzeniu zapytań profilowych, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="794d0-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<bookmarkResumptionQueries>**](bookmarkresumptionqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bookmarkResumptionQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="794d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="794d0-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="794d0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="794d0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="794d0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="794d0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="794d0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="794d0-107">Attributes</span></span>  
  
|<span data-ttu-id="794d0-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="794d0-108">Attribute</span></span>|<span data-ttu-id="794d0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="794d0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="794d0-110">name</span><span class="sxs-lookup"><span data-stu-id="794d0-110">name</span></span>|<span data-ttu-id="794d0-111">Ciąg określający nazwę rekordu zakładki do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="794d0-111">A string that specifies the name of the bookmark record to subscribe to.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="794d0-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="794d0-112">Child Elements</span></span>  
 <span data-ttu-id="794d0-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="794d0-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="794d0-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="794d0-114">Parent Elements</span></span>  
  
|<span data-ttu-id="794d0-115">Element</span><span class="sxs-lookup"><span data-stu-id="794d0-115">Element</span></span>|<span data-ttu-id="794d0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="794d0-116">Description</span></span>|  
|-------------|-----------------|  
|[\<bookmarkResumptionQueries>](bookmarkresumptionqueries.md)|<span data-ttu-id="794d0-117">Reprezentuje kolekcję zapytań, które są używane do śledzenia wznowienie zakładki w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="794d0-117">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="794d0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="794d0-118">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.BookmarkResumptionQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.BookmarkResumptionQuery?displayProperty=nameWithType>
- [<span data-ttu-id="794d0-119">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="794d0-119">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="794d0-120">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="794d0-120">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
