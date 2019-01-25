---
title: '&lt;workflowRuntime&gt;'
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: 5560d74a5c69a01a2e05d4c2461a280244e4cd0d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580619"
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="bf005-102">&lt;workflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="bf005-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="bf005-103">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> do hostingu opartego o przepływ pracy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bf005-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
 <span data-ttu-id="bf005-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bf005-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bf005-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="bf005-105">\<behaviors></span></span>  
<span data-ttu-id="bf005-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bf005-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bf005-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bf005-107">\<behavior></span></span>  
<span data-ttu-id="bf005-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="bf005-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf005-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf005-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf005-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bf005-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bf005-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bf005-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf005-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bf005-112">Attributes</span></span>  
  
|<span data-ttu-id="bf005-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bf005-113">Attribute</span></span>|<span data-ttu-id="bf005-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bf005-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bf005-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="bf005-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="bf005-116">Opcjonalny <xref:System.TimeSpan> wartość, która określa maksymalny czas pobytu wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim go jest wyładowania lub przerwania.</span><span class="sxs-lookup"><span data-stu-id="bf005-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="bf005-117">Jeśli ma workflowruntime `PersistenceService` który wykonuje unloadOnIdle, ten atrybut zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="bf005-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="bf005-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="bf005-118">enablePerformanceCounters</span></span>|<span data-ttu-id="bf005-119">Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone.</span><span class="sxs-lookup"><span data-stu-id="bf005-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="bf005-120">Liczniki wydajności zawierają informacje na temat różne statystyki związane z przepływu pracy, ale powodują spadek wydajności podczas uruchamiania aparatu wykonawczego przepływów pracy i wystąpienia przepływu pracy są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="bf005-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="bf005-121">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="bf005-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="bf005-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="bf005-122">name</span></span>|<span data-ttu-id="bf005-123">Ciąg zawierający nazwę aparatu wykonawczego przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="bf005-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="bf005-124">Nazwa jest używana w danych wyjściowych, aby odróżnić to środowisko wykonawcze od innych środowisk wykonawczych, które mogą być uruchomione w systemie, na przykład liczniki wydajności.</span><span class="sxs-lookup"><span data-stu-id="bf005-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="bf005-125">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="bf005-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="bf005-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="bf005-126">validateOnCreate</span></span>|<span data-ttu-id="bf005-127">Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi przy otwarciu WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="bf005-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="bf005-128">Jeśli ten atrybut jest równa `true`, walidacji przepływu pracy jest wykonywana w każdym `WorkflowServiceHost.Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="bf005-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="bf005-129">Jeśli zostaną znalezione błędy sprawdzania poprawności, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="bf005-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="bf005-130">Jeśli ta właściwość jest równa `false`, nastąpi nie nastąpi sprawdzanie poprawności definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bf005-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="bf005-131">Wartość domyślna tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="bf005-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf005-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bf005-132">Child Elements</span></span>  
  
|<span data-ttu-id="bf005-133">Element</span><span class="sxs-lookup"><span data-stu-id="bf005-133">Element</span></span>|<span data-ttu-id="bf005-134">Opis</span><span class="sxs-lookup"><span data-stu-id="bf005-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf005-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="bf005-135">commonParameters</span></span>|<span data-ttu-id="bf005-136">Kolekcja wspólnych parametrów używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="bf005-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="bf005-137">Ta kolekcja zwykle będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.</span><span class="sxs-lookup"><span data-stu-id="bf005-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="bf005-138">usługi</span><span class="sxs-lookup"><span data-stu-id="bf005-138">services</span></span>|<span data-ttu-id="bf005-139">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="bf005-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="bf005-140">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bf005-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="bf005-141">Usługi określone w kolekcji zostanie zainicjowany przez aparatu wykonawczego przepływów pracy i dodane do swoich usług przy odpowiednim <xref:System.Workflow.Runtime.WorkflowRuntime> wywoływany jest Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="bf005-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="bf005-142">W związku z tym usług określonych w kolekcji, należy wykonać niektóre zasady sposobu podpisy ich konstruktory.</span><span class="sxs-lookup"><span data-stu-id="bf005-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="bf005-143">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="bf005-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bf005-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bf005-144">Parent Elements</span></span>  
  
|<span data-ttu-id="bf005-145">Element</span><span class="sxs-lookup"><span data-stu-id="bf005-145">Element</span></span>|<span data-ttu-id="bf005-146">Opis</span><span class="sxs-lookup"><span data-stu-id="bf005-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf005-147">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="bf005-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bf005-148">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="bf005-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf005-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf005-149">Remarks</span></span>  
 <span data-ttu-id="bf005-150">Aby uzyskać więcej informacji na temat korzystania z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="bf005-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf005-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="bf005-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf005-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf005-152">See also</span></span>
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="bf005-153">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf005-153">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
