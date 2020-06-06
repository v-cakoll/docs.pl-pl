---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398957"
---
# \<activityStateQueries>
<span data-ttu-id="4d3ff-101">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-101">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="4d3ff-102">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-102">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="4d3ff-103">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-103">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="4d3ff-104">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-104">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="4d3ff-105">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4d3ff-105">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="4d3ff-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d3ff-106">Syntax</span></span>  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d3ff-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4d3ff-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4d3ff-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d3ff-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4d3ff-109">Attributes</span></span>  
 <span data-ttu-id="4d3ff-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d3ff-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4d3ff-111">Child Elements</span></span>  
  
|<span data-ttu-id="4d3ff-112">Element</span><span class="sxs-lookup"><span data-stu-id="4d3ff-112">Element</span></span>|<span data-ttu-id="4d3ff-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4d3ff-113">Description</span></span>|  
|-------------|-----------------|  
|[\<activityStateQuery>](activitystatequery.md)|<span data-ttu-id="4d3ff-114">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-114">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="4d3ff-115">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="4d3ff-115">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d3ff-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4d3ff-116">Parent Elements</span></span>  
  
|<span data-ttu-id="4d3ff-117">Element</span><span class="sxs-lookup"><span data-stu-id="4d3ff-117">Element</span></span>|<span data-ttu-id="4d3ff-118">Opis</span><span class="sxs-lookup"><span data-stu-id="4d3ff-118">Description</span></span>|  
|-------------|-----------------|  
|[\<workflow>](workflow.md)|<span data-ttu-id="4d3ff-119">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="4d3ff-119">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d3ff-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d3ff-120">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4d3ff-121">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4d3ff-121">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4d3ff-122">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4d3ff-122">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
