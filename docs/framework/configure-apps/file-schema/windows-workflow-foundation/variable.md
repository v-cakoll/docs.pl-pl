---
title: <variable>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
ms.openlocfilehash: 5878720f51f4b5cfe3163abf316a867ccda31342
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397769"
---
# \<variable>
<span data-ttu-id="4c4c9-101">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-101">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="4c4c9-102">Aby uzyskać więcej informacji na temat śledzenia kwerend profilu, zobacz [śledzenie profilów](../../../windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="4c4c9-102">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflow>**](workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQueries>**](activitystatequeries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<activityStateQuery>**](activitystatequery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<variables>**](variables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<variable>**  
  
## <a name="syntax"></a><span data-ttu-id="4c4c9-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c4c9-103">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c4c9-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4c4c9-104">Attributes and Elements</span></span>  
 <span data-ttu-id="4c4c9-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c4c9-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4c4c9-106">Attributes</span></span>  
  
|<span data-ttu-id="4c4c9-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4c4c9-107">Attribute</span></span>|<span data-ttu-id="4c4c9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="4c4c9-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c4c9-109">name</span><span class="sxs-lookup"><span data-stu-id="4c4c9-109">name</span></span>|<span data-ttu-id="4c4c9-110">Ciąg określający nazwę zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-110">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c4c9-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4c4c9-111">Child Elements</span></span>  
 <span data-ttu-id="4c4c9-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c4c9-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4c4c9-113">Parent Elements</span></span>  
  
|<span data-ttu-id="4c4c9-114">Element</span><span class="sxs-lookup"><span data-stu-id="4c4c9-114">Element</span></span>|<span data-ttu-id="4c4c9-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4c4c9-115">Description</span></span>|  
|-------------|-----------------|  
|[\<variable>](variable.md)|<span data-ttu-id="4c4c9-116">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-116">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c4c9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c4c9-117">Remarks</span></span>  
 <span data-ttu-id="4c4c9-118">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-118">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="4c4c9-119">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-119">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="4c4c9-120">Można użyć [\<arguments>](arguments.md) [\<states>](states.md) elementów i, [\<states>](states.md) Aby wyodrębnić dowolną zmienną lub argument z dowolnego działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-120">You can use the [\<arguments>](arguments.md), [\<states>](states.md) and [\<states>](states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="4c4c9-121">W poniższym przykładzie przedstawiono zapytanie o stan działania, które wyodrębnia zmienne i argumenty podczas `Closed` emitowania rekordu śledzenia działania.</span><span class="sxs-lookup"><span data-stu-id="4c4c9-121">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="4c4c9-122">Zmienne i argumenty mogą być wyodrębniane tylko za pomocą ActivityStateRecord i w ten sposób są subskrybowane w ramach profilu śledzenia przy użyciu [\<activityStateQuery>](activitystatequery.md) .</span><span class="sxs-lookup"><span data-stu-id="4c4c9-122">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c4c9-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c4c9-123">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [<span data-ttu-id="4c4c9-124">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="4c4c9-124">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4c4c9-125">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="4c4c9-125">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
