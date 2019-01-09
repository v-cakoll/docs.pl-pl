---
title: '&lt;add&gt; w &lt;services&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 9a86b7549e0efef10cbeb16dcc427d04065e43d3
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145539"
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="bd02b-102">&lt;add&gt; w &lt;services&gt;</span><span class="sxs-lookup"><span data-stu-id="bd02b-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="bd02b-103">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> do hostingu opartego o przepływ pracy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bd02b-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="bd02b-104">Ten element jest typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bd02b-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="bd02b-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd02b-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd02b-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bd02b-106">\<behaviors></span></span>  
<span data-ttu-id="bd02b-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bd02b-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="bd02b-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bd02b-108">\<behavior></span></span>  
<span data-ttu-id="bd02b-109">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="bd02b-109">\<services></span></span>  
<span data-ttu-id="bd02b-110">\<add></span><span class="sxs-lookup"><span data-stu-id="bd02b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd02b-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd02b-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd02b-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bd02b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="bd02b-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bd02b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd02b-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bd02b-114">Attributes</span></span>  
  
|<span data-ttu-id="bd02b-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bd02b-115">Attribute</span></span>|<span data-ttu-id="bd02b-116">Opis</span><span class="sxs-lookup"><span data-stu-id="bd02b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd02b-117">— typ</span><span class="sxs-lookup"><span data-stu-id="bd02b-117">type</span></span>|<span data-ttu-id="bd02b-118">Ciąg określający nazwę typu kwalifikowanego zestawu usługi do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="bd02b-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="bd02b-119">Określona usługa należy wykonać niektóre zasady sposobu podpisy ich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="bd02b-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="bd02b-120">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bd02b-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd02b-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bd02b-121">Child Elements</span></span>  
 <span data-ttu-id="bd02b-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="bd02b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd02b-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bd02b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="bd02b-124">Element</span><span class="sxs-lookup"><span data-stu-id="bd02b-124">Element</span></span>|<span data-ttu-id="bd02b-125">Opis</span><span class="sxs-lookup"><span data-stu-id="bd02b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd02b-126">\<usługi ></span><span class="sxs-lookup"><span data-stu-id="bd02b-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="bd02b-127">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="bd02b-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="bd02b-128">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bd02b-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="bd02b-129">Usługi określone w kolekcji zostanie zainicjowany przez aparatu wykonawczego przepływów pracy i dodane do swoich usług przy odpowiednim <xref:System.Workflow.Runtime.WorkflowRuntime> wywoływany jest Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="bd02b-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="bd02b-130">W związku z tym usług określonych w kolekcji, należy wykonać niektóre zasady sposobu podpisy ich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="bd02b-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="bd02b-131">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bd02b-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd02b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd02b-132">Remarks</span></span>  
 <span data-ttu-id="bd02b-133">Określona w tym elemencie usługa zostanie zainicjowany przez aparatu wykonawczego przepływów pracy i dodane do swoich usług przy odpowiednim <xref:System.Workflow.Runtime.WorkflowRuntime> wywoływany jest Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="bd02b-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="bd02b-134">W związku z tym określona usługa należy wykonać niektóre zasady sposobu podpisy ich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="bd02b-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="bd02b-135">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bd02b-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd02b-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd02b-136">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="bd02b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd02b-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <span data-ttu-id="bd02b-138">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bd02b-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
