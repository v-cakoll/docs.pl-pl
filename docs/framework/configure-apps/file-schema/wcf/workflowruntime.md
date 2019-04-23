---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: db5e1083c07d4e204eb19eaae9257ed44439132e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206567"
---
# <a name="workflowruntime"></a><span data-ttu-id="c1b2a-101">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="c1b2a-101">\<workflowRuntime></span></span>
<span data-ttu-id="c1b2a-102">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> do hostingu opartego o przepływ pracy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c1b2a-102">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="c1b2a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c1b2a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1b2a-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="c1b2a-104">\<behaviors></span></span>  
<span data-ttu-id="c1b2a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1b2a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="c1b2a-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c1b2a-106">\<behavior></span></span>  
<span data-ttu-id="c1b2a-107">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="c1b2a-107">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b2a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1b2a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1b2a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c1b2a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c1b2a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1b2a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c1b2a-111">Attributes</span></span>  
  
|<span data-ttu-id="c1b2a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c1b2a-112">Attribute</span></span>|<span data-ttu-id="c1b2a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c1b2a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1b2a-114">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="c1b2a-114">cachedInstanceExpiration</span></span>|<span data-ttu-id="c1b2a-115">Opcjonalny <xref:System.TimeSpan> wartość, która określa maksymalny czas pobytu wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim go jest wyładowania lub przerwania.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-115">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="c1b2a-116">Jeśli ma workflowruntime `PersistenceService` który wykonuje unloadOnIdle, ten atrybut zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-116">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="c1b2a-117">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="c1b2a-117">enablePerformanceCounters</span></span>|<span data-ttu-id="c1b2a-118">Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-118">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="c1b2a-119">Liczniki wydajności zawierają informacje na temat różne statystyki związane z przepływu pracy, ale powodują spadek wydajności podczas uruchamiania aparatu wykonawczego przepływów pracy i wystąpienia przepływu pracy są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-119">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="c1b2a-120">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-120">The default value is `true`.</span></span>|  
|<span data-ttu-id="c1b2a-121">nazwa</span><span class="sxs-lookup"><span data-stu-id="c1b2a-121">name</span></span>|<span data-ttu-id="c1b2a-122">Ciąg zawierający nazwę aparatu wykonawczego przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-122">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="c1b2a-123">Nazwa jest używana w danych wyjściowych, aby odróżnić to środowisko wykonawcze od innych środowisk wykonawczych, które mogą być uruchomione w systemie, na przykład liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-123">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="c1b2a-124">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-124">The default is an empty string.</span></span>|  
|<span data-ttu-id="c1b2a-125">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="c1b2a-125">validateOnCreate</span></span>|<span data-ttu-id="c1b2a-126">Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi przy otwarciu WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-126">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="c1b2a-127">Jeśli ten atrybut jest równa `true`, walidacji przepływu pracy jest wykonywana w każdym `WorkflowServiceHost.Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-127">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="c1b2a-128">Jeśli zostaną znalezione błędy sprawdzania poprawności, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-128">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="c1b2a-129">Jeśli ta właściwość jest równa `false`, nastąpi nie nastąpi sprawdzanie poprawności definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-129">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="c1b2a-130">Wartość domyślna tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-130">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1b2a-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c1b2a-131">Child Elements</span></span>  
  
|<span data-ttu-id="c1b2a-132">Element</span><span class="sxs-lookup"><span data-stu-id="c1b2a-132">Element</span></span>|<span data-ttu-id="c1b2a-133">Opis</span><span class="sxs-lookup"><span data-stu-id="c1b2a-133">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1b2a-134">commonParameters</span><span class="sxs-lookup"><span data-stu-id="c1b2a-134">commonParameters</span></span>|<span data-ttu-id="c1b2a-135">Kolekcja wspólnych parametrów używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-135">A collection of common parameters used by services.</span></span> <span data-ttu-id="c1b2a-136">Ta kolekcja zwykle będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-136">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="c1b2a-137">usługi</span><span class="sxs-lookup"><span data-stu-id="c1b2a-137">services</span></span>|<span data-ttu-id="c1b2a-138">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-138">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="c1b2a-139">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-139">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="c1b2a-140">Usługi określone w kolekcji zostanie zainicjowany przez aparatu wykonawczego przepływów pracy i dodane do swoich usług przy odpowiednim <xref:System.Workflow.Runtime.WorkflowRuntime> wywoływany jest Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-140">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c1b2a-141">W związku z tym usług określonych w kolekcji, należy wykonać niektóre zasady sposobu podpisy ich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-141">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c1b2a-142">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-142">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1b2a-143">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c1b2a-143">Parent Elements</span></span>  
  
|<span data-ttu-id="c1b2a-144">Element</span><span class="sxs-lookup"><span data-stu-id="c1b2a-144">Element</span></span>|<span data-ttu-id="c1b2a-145">Opis</span><span class="sxs-lookup"><span data-stu-id="c1b2a-145">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1b2a-146">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="c1b2a-146">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="c1b2a-147">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="c1b2a-147">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b2a-148">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1b2a-148">Remarks</span></span>  
 <span data-ttu-id="c1b2a-149">Aby uzyskać więcej informacji na temat korzystania z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c1b2a-149">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b2a-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1b2a-150">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c1b2a-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1b2a-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="c1b2a-152">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c1b2a-152">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
