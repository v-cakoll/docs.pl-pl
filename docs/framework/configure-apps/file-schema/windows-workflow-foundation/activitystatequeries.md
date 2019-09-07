---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: 58e3752be81609e32eee631e46d10c0a7d704248
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398957"
---
# <a name="activitystatequeries"></a><span data-ttu-id="57260-101">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="57260-101">\<activityStateQueries></span></span>
<span data-ttu-id="57260-102">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="57260-102">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="57260-103">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="57260-103">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="57260-104">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="57260-104">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="57260-105">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="57260-105">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
 <span data-ttu-id="57260-106">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="57260-106">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="57260-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57260-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57260-108">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57260-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="57260-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="57260-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="57260-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="57260-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="57260-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow.md)</span><span class="sxs-lookup"><span data-stu-id="57260-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)</span></span>\
<span data-ttu-id="57260-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="57260-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57260-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="57260-113">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57260-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57260-114">Attributes and Elements</span></span>  
 <span data-ttu-id="57260-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="57260-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57260-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57260-116">Attributes</span></span>  
 <span data-ttu-id="57260-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="57260-117">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57260-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57260-118">Child Elements</span></span>  
  
|<span data-ttu-id="57260-119">Element</span><span class="sxs-lookup"><span data-stu-id="57260-119">Element</span></span>|<span data-ttu-id="57260-120">Opis</span><span class="sxs-lookup"><span data-stu-id="57260-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57260-121">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="57260-121">\<activityStateQuery></span></span>](activitystatequery.md)|<span data-ttu-id="57260-122">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="57260-122">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="57260-123">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="57260-123">This event occurs each time a FaultHandler processes a fault.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57260-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57260-124">Parent Elements</span></span>  
  
|<span data-ttu-id="57260-125">Element</span><span class="sxs-lookup"><span data-stu-id="57260-125">Element</span></span>|<span data-ttu-id="57260-126">Opis</span><span class="sxs-lookup"><span data-stu-id="57260-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57260-127">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="57260-127">\<workflow></span></span>](workflow.md)|<span data-ttu-id="57260-128">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowanego przez właściwość **activityDefinitionId** .</span><span class="sxs-lookup"><span data-stu-id="57260-128">A configuration element that contains all queries for a specific workflow identified by the **activityDefinitionId** property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57260-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57260-129">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="57260-130">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="57260-130">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="57260-131">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="57260-131">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
