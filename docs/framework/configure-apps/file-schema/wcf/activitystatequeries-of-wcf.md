---
title: <activityStateQueries>programu WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850569"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="06875-102">\<activityStateQueries > WCF</span><span class="sxs-lookup"><span data-stu-id="06875-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="06875-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06875-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="06875-104">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="06875-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="06875-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="06875-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="06875-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="06875-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="06875-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="06875-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="06875-108">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06875-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06875-109">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06875-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06875-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Śledzenie >** ](tracking-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="06875-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)</span></span>\
<span data-ttu-id="06875-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> profilów**</span><span class="sxs-lookup"><span data-stu-id="06875-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**</span></span>\
<span data-ttu-id="06875-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<trackingProfile >** ](trackingprofile-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="06875-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)</span></span>\
<span data-ttu-id="06875-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<przepływ pracy >** ](workflow-of-wcf.md)</span><span class="sxs-lookup"><span data-stu-id="06875-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)</span></span>\
<span data-ttu-id="06875-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<activityStateQueries >**</span><span class="sxs-lookup"><span data-stu-id="06875-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06875-115">Składnia</span><span class="sxs-lookup"><span data-stu-id="06875-115">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="06875-116">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06875-116">Attributes and elements</span></span>

<span data-ttu-id="06875-117">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06875-117">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="06875-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06875-118">Attributes</span></span>  

<span data-ttu-id="06875-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="06875-119">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="06875-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06875-120">Child elements</span></span>

|<span data-ttu-id="06875-121">Element</span><span class="sxs-lookup"><span data-stu-id="06875-121">Element</span></span>|<span data-ttu-id="06875-122">Opis</span><span class="sxs-lookup"><span data-stu-id="06875-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06875-123">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="06875-123">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="06875-124">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="06875-124">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="06875-125">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="06875-125">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06875-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06875-126">Parent elements</span></span>

|<span data-ttu-id="06875-127">Element</span><span class="sxs-lookup"><span data-stu-id="06875-127">Element</span></span>|<span data-ttu-id="06875-128">Opis</span><span class="sxs-lookup"><span data-stu-id="06875-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06875-129">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="06875-129">\<workflow></span></span>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="06875-130">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="06875-130">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="06875-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06875-131">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="06875-132">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="06875-132">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="06875-133">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="06875-133">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
