---
title: <add> dla <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 38dec132626b97accacea1b7007d914edcab0abc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926657"
---
# <a name="add-of-services"></a><span data-ttu-id="67fb8-102">\<Dodawanie > \<usług ></span><span class="sxs-lookup"><span data-stu-id="67fb8-102">\<add> of \<services></span></span>
<span data-ttu-id="67fb8-103">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="67fb8-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="67fb8-104">Ten element jest typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="67fb8-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="67fb8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="67fb8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="67fb8-106">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="67fb8-106">\<behaviors></span></span>  
<span data-ttu-id="67fb8-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="67fb8-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="67fb8-108">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="67fb8-108">\<behavior></span></span>  
<span data-ttu-id="67fb8-109">\<> usług</span><span class="sxs-lookup"><span data-stu-id="67fb8-109">\<services></span></span>  
<span data-ttu-id="67fb8-110">\<add></span><span class="sxs-lookup"><span data-stu-id="67fb8-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67fb8-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="67fb8-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67fb8-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67fb8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="67fb8-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67fb8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67fb8-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67fb8-114">Attributes</span></span>  
  
|<span data-ttu-id="67fb8-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="67fb8-115">Attribute</span></span>|<span data-ttu-id="67fb8-116">Opis</span><span class="sxs-lookup"><span data-stu-id="67fb8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67fb8-117">— typ</span><span class="sxs-lookup"><span data-stu-id="67fb8-117">type</span></span>|<span data-ttu-id="67fb8-118">Ciąg określający nazwę typu kwalifikowanego zestawu usługi do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="67fb8-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="67fb8-119">Określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="67fb8-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="67fb8-120">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="67fb8-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67fb8-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67fb8-121">Child Elements</span></span>  
 <span data-ttu-id="67fb8-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="67fb8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67fb8-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67fb8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="67fb8-124">Element</span><span class="sxs-lookup"><span data-stu-id="67fb8-124">Element</span></span>|<span data-ttu-id="67fb8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="67fb8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="67fb8-126">\<> usług</span><span class="sxs-lookup"><span data-stu-id="67fb8-126">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="67fb8-127">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="67fb8-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="67fb8-128">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="67fb8-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="67fb8-129">Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy zostanie wywołany odpowiedni <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="67fb8-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="67fb8-130">W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="67fb8-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="67fb8-131">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="67fb8-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67fb8-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67fb8-132">Remarks</span></span>  
 <span data-ttu-id="67fb8-133">Usługa określona w tym elemencie zostanie zainicjowana przez aparat środowiska uruchomieniowego przepływu pracy i dodana do jej usług, <xref:System.Workflow.Runtime.WorkflowRuntime> gdy zostanie wywołany odpowiedni Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="67fb8-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="67fb8-134">W związku z tym określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="67fb8-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="67fb8-135">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="67fb8-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67fb8-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="67fb8-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67fb8-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67fb8-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="67fb8-138">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="67fb8-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
