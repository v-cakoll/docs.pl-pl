---
title: '&lt;Zmienne&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: da0fd144-dda9-4613-b650-fe6325076513
ms.openlocfilehash: 4dc7ab2dd15beb9707807147917c344e989be7f1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154128"
---
# <a name="ltvariablesgt"></a><span data-ttu-id="eb834-102">&lt;Zmienne&gt;</span><span class="sxs-lookup"><span data-stu-id="eb834-102">&lt;variables&gt;</span></span>
<span data-ttu-id="eb834-103">Reprezentuje kolekcję zmiennych skojarzoną z tym zapytaniem działania.</span><span class="sxs-lookup"><span data-stu-id="eb834-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="eb834-104">Aby uzyskać więcej informacji na podstawie śledzenia zapytań profilu zobacz [profile śledzenia](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="eb834-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="eb834-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb834-105">\<system.serviceModel></span></span>  
<span data-ttu-id="eb834-106">\<Śledzenie ></span><span class="sxs-lookup"><span data-stu-id="eb834-106">\<tracking></span></span>  
<span data-ttu-id="eb834-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="eb834-107">\<trackingProfile></span></span>  
<span data-ttu-id="eb834-108">\<przepływ pracy ></span><span class="sxs-lookup"><span data-stu-id="eb834-108">\<workflow></span></span>  
<span data-ttu-id="eb834-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="eb834-109">\<activityStateQueries></span></span>  
<span data-ttu-id="eb834-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="eb834-110">\<activityStateQuery></span></span>  
<span data-ttu-id="eb834-111">\<Zmienne ></span><span class="sxs-lookup"><span data-stu-id="eb834-111">\<variables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb834-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb834-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb834-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eb834-113">Attributes and Elements</span></span>  
 <span data-ttu-id="eb834-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb834-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb834-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eb834-115">Attributes</span></span>  
 <span data-ttu-id="eb834-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="eb834-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eb834-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eb834-117">Child Elements</span></span>  
  
|<span data-ttu-id="eb834-118">Element</span><span class="sxs-lookup"><span data-stu-id="eb834-118">Element</span></span>|<span data-ttu-id="eb834-119">Opis</span><span class="sxs-lookup"><span data-stu-id="eb834-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb834-120">\<Zmienna ></span><span class="sxs-lookup"><span data-stu-id="eb834-120">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="eb834-121">Zmienna skojarzonych z kwerendą stanu działania.</span><span class="sxs-lookup"><span data-stu-id="eb834-121">A variable associated with an activity state query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb834-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eb834-122">Parent Elements</span></span>  
  
|<span data-ttu-id="eb834-123">Element</span><span class="sxs-lookup"><span data-stu-id="eb834-123">Element</span></span>|<span data-ttu-id="eb834-124">Opis</span><span class="sxs-lookup"><span data-stu-id="eb834-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb834-125">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="eb834-125">\<activityStateQuery></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|<span data-ttu-id="eb834-126">Reprezentuje element konfiguracji, które jest używane do śledzenia żądań, aby anulować działanie podrzędne przez działanie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eb834-126">Represents a configuration element that is used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="eb834-127">Zapytanie jest niezbędne do uczestnika śledzenia do subskrybowania Anuluj żądanie rekordu obiektów.</span><span class="sxs-lookup"><span data-stu-id="eb834-127">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb834-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb834-128">Remarks</span></span>  
 <span data-ttu-id="eb834-129">Jedno rozwiązanie ActivityStateQuery jest możliwość wyodrębniania danych podczas śledzenia wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="eb834-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="eb834-130">Umożliwia to dodatkowy kontekst podczas uzyskiwania dostępu do śledzenia rekordów post wykonywania.</span><span class="sxs-lookup"><span data-stu-id="eb834-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="eb834-131">Możesz użyć [ \<argumenty >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) i [ \<stany >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementy, aby wyodrębnić dowolnej zmiennej lub argumentu wszelkie działania w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="eb834-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="eb834-132">W poniższym przykładzie pokazano kwerendą stanu działania, który wyodrębnia zmienne i argumenty podczas działania `Closed` rekord śledzenia jest emitowane.</span><span class="sxs-lookup"><span data-stu-id="eb834-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="eb834-133">Zmienne i argumenty wyodrębniania tylko z ActivityStateRecord i w związku z tym subskrybują w ramach śledzenia profilu przy użyciu [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="eb834-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eb834-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb834-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElementCollection?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="eb834-135">Kontrola i śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="eb834-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="eb834-136">Profile śledzenia</span><span class="sxs-lookup"><span data-stu-id="eb834-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
