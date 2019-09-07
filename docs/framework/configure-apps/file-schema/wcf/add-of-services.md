---
title: <add> dla <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398291"
---
# <a name="add-of-services"></a><span data-ttu-id="613ae-102">\<Dodawanie > \<usług ></span><span class="sxs-lookup"><span data-stu-id="613ae-102">\<add> of \<services></span></span>
<span data-ttu-id="613ae-103">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="613ae-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="613ae-104">Ten element jest typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="613ae-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
<span data-ttu-id="613ae-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="613ae-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="613ae-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="613ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="613ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="613ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="613ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services-of-workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="613ae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)</span></span>\
<span data-ttu-id="613ae-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="613ae-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613ae-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="613ae-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="613ae-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="613ae-114">Attributes and Elements</span></span>  
 <span data-ttu-id="613ae-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="613ae-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="613ae-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="613ae-116">Attributes</span></span>  
  
|<span data-ttu-id="613ae-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="613ae-117">Attribute</span></span>|<span data-ttu-id="613ae-118">Opis</span><span class="sxs-lookup"><span data-stu-id="613ae-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="613ae-119">— typ</span><span class="sxs-lookup"><span data-stu-id="613ae-119">type</span></span>|<span data-ttu-id="613ae-120">Ciąg określający nazwę typu kwalifikowanego zestawu usługi do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="613ae-120">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="613ae-121">Określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="613ae-121">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="613ae-122">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="613ae-122">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="613ae-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="613ae-123">Child Elements</span></span>  
 <span data-ttu-id="613ae-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="613ae-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="613ae-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="613ae-125">Parent Elements</span></span>  
  
|<span data-ttu-id="613ae-126">Element</span><span class="sxs-lookup"><span data-stu-id="613ae-126">Element</span></span>|<span data-ttu-id="613ae-127">Opis</span><span class="sxs-lookup"><span data-stu-id="613ae-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="613ae-128">\<> usług</span><span class="sxs-lookup"><span data-stu-id="613ae-128">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="613ae-129">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="613ae-129">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="613ae-130">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="613ae-130">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="613ae-131">Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy zostanie wywołany odpowiedni <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="613ae-131">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="613ae-132">W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="613ae-132">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="613ae-133">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="613ae-133">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="613ae-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="613ae-134">Remarks</span></span>  
 <span data-ttu-id="613ae-135">Usługa określona w tym elemencie zostanie zainicjowana przez aparat środowiska uruchomieniowego przepływu pracy i dodana do jej usług, <xref:System.Workflow.Runtime.WorkflowRuntime> gdy zostanie wywołany odpowiedni Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="613ae-135">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="613ae-136">W związku z tym określona usługa musi być zgodna z określonymi regułami dotyczącymi podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="613ae-136">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="613ae-137">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="613ae-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="613ae-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="613ae-138">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="613ae-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="613ae-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="613ae-140">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="613ae-140">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
