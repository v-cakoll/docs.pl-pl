---
title: '&lt;add&gt; w &lt;services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a859676adf48fda05040633fb8909d161e9ce8e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="ae19a-102">&lt;add&gt; w &lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="ae19a-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="ae19a-103">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu opartego o przepływ pracy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="ae19a-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="ae19a-104">Ten element jest typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae19a-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="ae19a-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ae19a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae19a-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="ae19a-106">\<behaviors></span></span>  
<span data-ttu-id="ae19a-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ae19a-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="ae19a-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="ae19a-108">\<behavior></span></span>  
<span data-ttu-id="ae19a-109">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="ae19a-109">\<services></span></span>  
<span data-ttu-id="ae19a-110">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="ae19a-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae19a-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae19a-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae19a-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ae19a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ae19a-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ae19a-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae19a-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ae19a-114">Attributes</span></span>  
  
|<span data-ttu-id="ae19a-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ae19a-115">Attribute</span></span>|<span data-ttu-id="ae19a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="ae19a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae19a-117">— typ</span><span class="sxs-lookup"><span data-stu-id="ae19a-117">type</span></span>|<span data-ttu-id="ae19a-118">Ciąg określający nazwę typu kwalifikowanego zestawu usługi do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="ae19a-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="ae19a-119">Określona usługa należy wykonać niektóre zasady dotyczące podpisy ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="ae19a-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="ae19a-120">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae19a-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae19a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ae19a-121">Child Elements</span></span>  
 <span data-ttu-id="ae19a-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="ae19a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae19a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ae19a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ae19a-124">Element</span><span class="sxs-lookup"><span data-stu-id="ae19a-124">Element</span></span>|<span data-ttu-id="ae19a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="ae19a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae19a-126">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="ae19a-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="ae19a-127">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="ae19a-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="ae19a-128">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae19a-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="ae19a-129">Usług określonych w kolekcji zostanie zainicjowany przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do jej usług podczas odpowiednie <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="ae19a-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="ae19a-130">W związku z tym usługi określona w kolekcji należy wykonać niektóre zasady dotyczące podpisy ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="ae19a-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="ae19a-131">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae19a-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae19a-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae19a-132">Remarks</span></span>  
 <span data-ttu-id="ae19a-133">Usługi określone w tym elemencie zostanie zainicjowany przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do jej usług podczas odpowiednie <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="ae19a-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="ae19a-134">W związku z tym określona usługa należy wykonać niektóre zasady dotyczące podpisy ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="ae19a-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="ae19a-135">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae19a-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae19a-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae19a-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae19a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae19a-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="ae19a-138">Pliki konfiguracji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="ae19a-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
