---
title: <cancelRequestedQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8da9b1c4-338a-4f23-9830-6d257772d340
ms.openlocfilehash: 3e6840ce647625c36356cccd4651f17de32777e2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152290"
---
# \<cancelRequestedQuery>
<span data-ttu-id="8b526-101">Reprezentuje zapytanie, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b526-101">Represents a query that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8b526-102">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8b526-102">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>  
  
 <span data-ttu-id="8b526-103">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8b526-103">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cancelRequestedQueries>**](cancelrequestedqueries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cancelRequestedQuery>**  
  
## <a name="syntax"></a><span data-ttu-id="8b526-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b526-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b526-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8b526-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8b526-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b526-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b526-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b526-107">Attributes</span></span>  
  
|<span data-ttu-id="8b526-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8b526-108">Attribute</span></span>|<span data-ttu-id="8b526-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8b526-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b526-110">activityName</span><span class="sxs-lookup"><span data-stu-id="8b526-110">activityName</span></span>|<span data-ttu-id="8b526-111">Ciąg określający nazwę działania, który żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="8b526-111">A string that specifies the name of the activity that is requesting the cancellation.</span></span>|  
|<span data-ttu-id="8b526-112">childActivityName</span><span class="sxs-lookup"><span data-stu-id="8b526-112">childActivityName</span></span>|<span data-ttu-id="8b526-113">Ciąg, który określa nazwę działania podrzędnego, dla której zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="8b526-113">A string that specifies the name of the child activity for which cancellation was requested.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b526-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8b526-114">Child Elements</span></span>  
 <span data-ttu-id="8b526-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="8b526-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b526-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b526-116">Parent Elements</span></span>  
  
|<span data-ttu-id="8b526-117">Element</span><span class="sxs-lookup"><span data-stu-id="8b526-117">Element</span></span>|<span data-ttu-id="8b526-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8b526-118">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="8b526-119">Reprezentuje listę elementów konfiguracji, które są używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b526-119">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="8b526-120">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="8b526-120">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8b526-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b526-121">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CancelRequestedQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CancelRequestedQuery?displayProperty=nameWithType>
- [<span data-ttu-id="8b526-122">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b526-122">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="8b526-123">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="8b526-123">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
