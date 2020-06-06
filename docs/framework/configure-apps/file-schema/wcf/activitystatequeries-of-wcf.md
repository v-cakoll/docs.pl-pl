---
title: <activityStateQueries>programu WCF
ms.date: 10/08/2018
ms.assetid: 9e45db49-ed85-4fdf-bd65-0d5477e31823
ms.openlocfilehash: 249ac3d91f6251a943dd856e4122b8b54f691702
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850569"
---
# <a name="activitystatequeries-of-wcf"></a><span data-ttu-id="d34ce-102">\<activityStateQueries>programu WCF</span><span class="sxs-lookup"><span data-stu-id="d34ce-102">\<activityStateQueries> of WCF</span></span>

<span data-ttu-id="d34ce-103">Reprezentuje kolekcję zapytań, które są używane do śledzenia zmian cyklem życia działań, które tworzą wystąpienie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d34ce-103">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="d34ce-104">Na przykład możesz chcieć śledzić każde działanie "Wyślij wiadomość E-Mail" w ramach wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="d34ce-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="d34ce-105">To zapytanie jest niezbędne do śledzenia uczestnika do subskrybowania obiektów rekordu stanu działania.</span><span class="sxs-lookup"><span data-stu-id="d34ce-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="d34ce-106">Stany do subskrybowania są wyszczególnione w ActivityStates.</span><span class="sxs-lookup"><span data-stu-id="d34ce-106">The available states to subscribe to are specified in ActivityStates.</span></span>

<span data-ttu-id="d34ce-107">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d34ce-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<profiles>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow-of-wcf.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<activityStateQueries>**  
  
## <a name="syntax"></a><span data-ttu-id="d34ce-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="d34ce-108">Syntax</span></span>  
  
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

## <a name="attributes-and-elements"></a><span data-ttu-id="d34ce-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d34ce-109">Attributes and elements</span></span>

<span data-ttu-id="d34ce-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d34ce-110">The following sections describe attributes, child elements, and parent elements.</span></span>
  
### <a name="attributes"></a><span data-ttu-id="d34ce-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d34ce-111">Attributes</span></span>  

<span data-ttu-id="d34ce-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="d34ce-112">None.</span></span>  

### <a name="child-elements"></a><span data-ttu-id="d34ce-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d34ce-113">Child elements</span></span>

|<span data-ttu-id="d34ce-114">Element</span><span class="sxs-lookup"><span data-stu-id="d34ce-114">Element</span></span>|<span data-ttu-id="d34ce-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d34ce-115">Description</span></span>|
|-------------|-----------------|
|[\<activityStateQuery>](activitystatequery-of-wcf.md)|<span data-ttu-id="d34ce-116">Zapytanie, które jest używane do śledzenia obsługi błędów występujących w ramach działania.</span><span class="sxs-lookup"><span data-stu-id="d34ce-116">A query that is used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="d34ce-117">To zdarzenie jest wykonywane za każdym razem, gdy FaultHandler przetwarza błąd.</span><span class="sxs-lookup"><span data-stu-id="d34ce-117">This event occurs each time a FaultHandler processes a fault.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d34ce-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d34ce-118">Parent elements</span></span>

|<span data-ttu-id="d34ce-119">Element</span><span class="sxs-lookup"><span data-stu-id="d34ce-119">Element</span></span>|<span data-ttu-id="d34ce-120">Opis</span><span class="sxs-lookup"><span data-stu-id="d34ce-120">Description</span></span>|
|-------------|-----------------|
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<span data-ttu-id="d34ce-121">Element konfiguracji, który zawiera wszystkie zapytania dla określonego przepływu pracy identyfikowane przez `activityDefinitionId` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d34ce-121">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d34ce-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d34ce-122">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="d34ce-123">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="d34ce-123">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="d34ce-124">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="d34ce-124">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
