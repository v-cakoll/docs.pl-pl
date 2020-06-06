---
title: <cancelRequestedQuery>programu WCF
ms.date: 03/30/2017
ms.assetid: b690d870-02eb-4c56-8bc3-e5ca99d7097b
ms.openlocfilehash: 0ac8b87afc44927ab6653dd6fcdc09cd61436a9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850049"
---
# <a name="cancelrequestedquery-of-wcf"></a><span data-ttu-id="4c023-102">\<cancelRequestedQuery>programu WCF</span><span class="sxs-lookup"><span data-stu-id="4c023-102">\<cancelRequestedQuery> of WCF</span></span>

<span data-ttu-id="4c023-103">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c023-103">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="4c023-104">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="4c023-104">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
<span data-ttu-id="4c023-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4c023-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  

## <a name="syntax"></a><span data-ttu-id="4c023-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c023-106">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestedQueries>
          <cancelRequestedQuery activityName="String"
                                childActivityName="String" />
        </cancelRequestedQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c023-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4c023-107">Attributes and elements</span></span>

<span data-ttu-id="4c023-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c023-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4c023-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4c023-109">Attributes</span></span>  
  
|<span data-ttu-id="4c023-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4c023-110">Attribute</span></span>|<span data-ttu-id="4c023-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4c023-111">Description</span></span>|  
|---------------|-----------------|  
|`activityName`|<span data-ttu-id="4c023-112">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="4c023-112">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|`childActivityName`|<span data-ttu-id="4c023-113">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="4c023-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c023-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4c023-114">Child elements</span></span>

<span data-ttu-id="4c023-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="4c023-115">None.</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="4c023-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4c023-116">Parent elements</span></span>
  
|<span data-ttu-id="4c023-117">Element</span><span class="sxs-lookup"><span data-stu-id="4c023-117">Element</span></span>|<span data-ttu-id="4c023-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4c023-118">Description</span></span>|  
|-------------|-----------------|  
|[\<cancelRequestedQueries>](cancelrequestedqueries-of-wcf.md)|<span data-ttu-id="4c023-119">Reprezentuje kolekcję zapytań, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c023-119">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c023-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c023-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4c023-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4c023-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4c023-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4c023-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
