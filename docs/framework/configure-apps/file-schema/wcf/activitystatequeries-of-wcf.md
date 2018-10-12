---
title: '&lt;activityStateQueries&gt; w WCF'
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 081dc297912ed5735dd51111936b85b61f463d2d
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123244"
---
# <a name="ltactivitystatequeriesgt-of-wcf"></a><span data-ttu-id="2fa31-102">&lt;activityStateQueries&gt; w WCF</span><span class="sxs-lookup"><span data-stu-id="2fa31-102">&lt;activityStateQueries&gt; of WCF</span></span>

<span data-ttu-id="2fa31-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2fa31-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="2fa31-104">Na przykład chcesz do śledzenia za każdym razem, gdy kończy działanie "Wyślij wiadomość E-Mail", w ramach wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="2fa31-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="2fa31-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="2fa31-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="2fa31-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="2fa31-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="2fa31-107">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="2fa31-107">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="2fa31-108">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2fa31-108">\<system.serviceModel></span></span>  
<span data-ttu-id="2fa31-109">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="2fa31-109">\<tracking></span></span>  
<span data-ttu-id="2fa31-110">\<profile ></span><span class="sxs-lookup"><span data-stu-id="2fa31-110">\<profiles></span></span>  
<span data-ttu-id="2fa31-111">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="2fa31-111">\<trackingProfile></span></span>  
<span data-ttu-id="2fa31-112">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2fa31-112">\<workflow></span></span>  
<span data-ttu-id="2fa31-113">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="2fa31-113">\<activityStateQueries></span></span>  

## <a name="syntax"></a><span data-ttu-id="2fa31-114">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa31-114">Syntax</span></span>  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String"/>
            </arguments>
            <states>
              <state name="String"/>
            </states>
            <variables>
              <variable name="String"/>
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  

## <a name="attributes-and-elements"></a><span data-ttu-id="2fa31-115">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2fa31-115">Attributes and elements</span></span>

<span data-ttu-id="2fa31-116">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2fa31-116">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="2fa31-117">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2fa31-117">Attributes</span></span>  

<span data-ttu-id="2fa31-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="2fa31-118">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="2fa31-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa31-119">Child elements</span></span>

|<span data-ttu-id="2fa31-120">Element</span><span class="sxs-lookup"><span data-stu-id="2fa31-120">Element</span></span>|<span data-ttu-id="2fa31-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa31-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fa31-122">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="2fa31-122">\<activityStateQuery></span></span>](activitystatequery-of-wcf.md)|<span data-ttu-id="2fa31-123">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="2fa31-123">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="2fa31-124">To zdarzenie występuje, każdym razem FaultHandler przetwarza błąd wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2fa31-124">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2fa31-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2fa31-125">Parent elements</span></span>

|<span data-ttu-id="2fa31-126">Element</span><span class="sxs-lookup"><span data-stu-id="2fa31-126">Element</span></span>|<span data-ttu-id="2fa31-127">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa31-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fa31-128">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="2fa31-128">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="2fa31-129">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="2fa31-129">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2fa31-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2fa31-130">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>    
- <xref:System.Activities.Tracking.ActivityStateQuery>    
- [<span data-ttu-id="2fa31-131">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="2fa31-131">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
- [<span data-ttu-id="2fa31-132">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="2fa31-132">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
