---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 0cd04f66cc4b73eb5f1c43bd6c8dc9189dfceff1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915213"
---
# <a name="workflowruntime"></a><span data-ttu-id="8e61c-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="8e61c-101">\<workflowRuntime></span></span>
<span data-ttu-id="8e61c-102">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="8e61c-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="8e61c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e61c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e61c-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="8e61c-104">\<behaviors></span></span>  
<span data-ttu-id="8e61c-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e61c-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8e61c-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="8e61c-106">\<behavior></span></span>  
<span data-ttu-id="8e61c-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="8e61c-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e61c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e61c-108">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"
                 enablePerformanceCounters="Boolean"
                 name="String"
                 validateOnCreate="Boolean">
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e61c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8e61c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8e61c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8e61c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e61c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8e61c-111">Attributes</span></span>  
  
|<span data-ttu-id="8e61c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8e61c-112">Attribute</span></span>|<span data-ttu-id="8e61c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8e61c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e61c-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="8e61c-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="8e61c-115">Opcjonalna <xref:System.TimeSpan> wartość, która określa maksymalny czas trwania wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim zostanie wymuszone zwolnione lub przerwane.</span><span class="sxs-lookup"><span data-stu-id="8e61c-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="8e61c-116">Jeśli element WorkflowRuntime ma `PersistenceService` unloadOnIdle, ten atrybut jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="8e61c-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="8e61c-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="8e61c-117">enablePerformanceCounters</span></span>|<span data-ttu-id="8e61c-118">Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone.</span><span class="sxs-lookup"><span data-stu-id="8e61c-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="8e61c-119">Liczniki wydajności dostarczają informacji na temat różnych statystyk związanych z przepływem pracy, ale powodują spadek wydajności, gdy uruchamiany jest aparat środowiska uruchomieniowego przepływu pracy i kiedy wystąpienia przepływu pracy są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="8e61c-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="8e61c-120">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="8e61c-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="8e61c-121">nazwa</span><span class="sxs-lookup"><span data-stu-id="8e61c-121">name</span></span>|<span data-ttu-id="8e61c-122">Ciąg zawierający nazwę aparatu środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e61c-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="8e61c-123">Nazwa jest używana w danych wyjściowych w celu odróżnienia tego środowiska uruchomieniowego od innych środowisk uruchomieniowych, które mogą być uruchomione w systemie, na przykład w licznikach wydajności.</span><span class="sxs-lookup"><span data-stu-id="8e61c-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="8e61c-124">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="8e61c-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="8e61c-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="8e61c-125">validateOnCreate</span></span>|<span data-ttu-id="8e61c-126">Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi po otwarciu obiektu WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="8e61c-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="8e61c-127">Gdy ten atrybut jest ustawiony na `true`, sprawdzanie poprawności przepływu pracy jest wykonywane za `WorkflowServiceHost.Open` każdym razem, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="8e61c-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="8e61c-128">Jeśli zostaną znalezione błędy walidacji, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="8e61c-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="8e61c-129">Gdy ta właściwość jest ustawiona na `false`, nie będzie wykonywane Walidacja definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8e61c-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="8e61c-130">Wartość domyślna tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="8e61c-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e61c-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8e61c-131">Child Elements</span></span>  
  
|<span data-ttu-id="8e61c-132">Element</span><span class="sxs-lookup"><span data-stu-id="8e61c-132">Element</span></span>|<span data-ttu-id="8e61c-133">Opis</span><span class="sxs-lookup"><span data-stu-id="8e61c-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e61c-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="8e61c-134">commonParameters</span></span>|<span data-ttu-id="8e61c-135">Kolekcja typowych parametrów używanych przez usługi.</span><span class="sxs-lookup"><span data-stu-id="8e61c-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="8e61c-136">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="8e61c-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="8e61c-137">usługi</span><span class="sxs-lookup"><span data-stu-id="8e61c-137">services</span></span>|<span data-ttu-id="8e61c-138">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="8e61c-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="8e61c-139">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8e61c-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="8e61c-140">Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy zostanie wywołany odpowiedni <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8e61c-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="8e61c-141">W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="8e61c-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="8e61c-142">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="8e61c-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e61c-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8e61c-143">Parent Elements</span></span>  
  
|<span data-ttu-id="8e61c-144">Element</span><span class="sxs-lookup"><span data-stu-id="8e61c-144">Element</span></span>|<span data-ttu-id="8e61c-145">Opis</span><span class="sxs-lookup"><span data-stu-id="8e61c-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e61c-146">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="8e61c-146">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8e61c-147">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="8e61c-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e61c-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e61c-148">Remarks</span></span>  
 <span data-ttu-id="8e61c-149">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8e61c-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e61c-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e61c-150">Example</span></span>  
  
```xml  
<serviceBehaviors>
   <behavior name="ServiceBehavior">
      <workflowRuntime name="WorkflowServiceHostRuntime"
                       validateOnCreate="true"
                       enablePerformanceCounters="true">
         <commonParameters>
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
            <add name="EnableRetries" value="True" />
         </commonParameters>
         <services>
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>
         </services>
      </workflowRuntime>
   </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="8e61c-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e61c-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="8e61c-152">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8e61c-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
