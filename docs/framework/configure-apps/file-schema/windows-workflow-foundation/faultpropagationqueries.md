---
title: <faultPropagationQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 00ff90ae-ebe0-4c85-a93f-61557288d0a3
ms.openlocfilehash: 3d6d03638ec5806448a16cc32b37e630d6198624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152134"
---
# \<faultPropagationQueries>
<span data-ttu-id="ffbd1-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-101">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ffbd1-102">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-102">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="ffbd1-103">Należy użyć takiej kwerendy do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-103">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="ffbd1-104">Zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania błędów propagacji rekordów.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-104">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>  
  
 <span data-ttu-id="ffbd1-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="ffbd1-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<faultPropagationQueries>**
  
## <a name="syntax"></a><span data-ttu-id="ffbd1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffbd1-106">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffbd1-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ffbd1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ffbd1-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffbd1-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ffbd1-109">Attributes</span></span>  
 <span data-ttu-id="ffbd1-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ffbd1-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ffbd1-111">Child Elements</span></span>  
  
|<span data-ttu-id="ffbd1-112">Element</span><span class="sxs-lookup"><span data-stu-id="ffbd1-112">Element</span></span>|<span data-ttu-id="ffbd1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ffbd1-113">Description</span></span>|  
|-------------|-----------------|  
|[\<faultPropagationQuery>](faultpropagationquery.md)|<span data-ttu-id="ffbd1-114">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="ffbd1-115">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="ffbd1-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ffbd1-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ffbd1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ffbd1-117">Element</span><span class="sxs-lookup"><span data-stu-id="ffbd1-117">Element</span></span>|<span data-ttu-id="ffbd1-118">Opis</span><span class="sxs-lookup"><span data-stu-id="ffbd1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="ffbd1-119">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="ffbd1-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffbd1-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ffbd1-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [<span data-ttu-id="ffbd1-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ffbd1-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="ffbd1-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="ffbd1-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
