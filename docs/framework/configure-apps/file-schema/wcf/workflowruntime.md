---
title: '&lt;Obiekt workflowRuntime&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: db891e9d967f4471e2b0a3778db433adb62e121c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltworkflowruntimegt"></a><span data-ttu-id="64d4f-102">&lt;Obiekt workflowRuntime&gt;</span><span class="sxs-lookup"><span data-stu-id="64d4f-102">&lt;workflowRuntime&gt;</span></span>
<span data-ttu-id="64d4f-103">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu opartego o przepływ pracy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="64d4f-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>  
  
 <span data-ttu-id="64d4f-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="64d4f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="64d4f-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="64d4f-105">\<behaviors></span></span>  
<span data-ttu-id="64d4f-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="64d4f-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="64d4f-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="64d4f-107">\<behavior></span></span>  
<span data-ttu-id="64d4f-108">\<Obiekt workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="64d4f-108">\<workflowRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d4f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="64d4f-109">Syntax</span></span>  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64d4f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64d4f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="64d4f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="64d4f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64d4f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64d4f-112">Attributes</span></span>  
  
|<span data-ttu-id="64d4f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="64d4f-113">Attribute</span></span>|<span data-ttu-id="64d4f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="64d4f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="64d4f-115">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="64d4f-115">cachedInstanceExpiration</span></span>|<span data-ttu-id="64d4f-116">Opcjonalny <xref:System.TimeSpan> wartość, która określa maksymalny czas trwania wystąpienia przepływu pracy mogą pozostać w pamięci w stanie bezczynności przed jej wymuszeniem wyładowania lub zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="64d4f-116">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="64d4f-117">Jeśli ma elementu workflowruntime `PersistenceService` który wykonuje unloadOnIdle, ten atrybut jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="64d4f-117">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="64d4f-118">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="64d4f-118">enablePerformanceCounters</span></span>|<span data-ttu-id="64d4f-119">Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone.</span><span class="sxs-lookup"><span data-stu-id="64d4f-119">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="64d4f-120">Liczniki wydajności zawierają informacje dotyczące różnych statystyki związane z przepływu pracy, ale ich spowodować spadek wydajności podczas uruchamiania aparatu wykonawczego workflow i uruchomionych wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="64d4f-120">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="64d4f-121">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="64d4f-121">The default value is `true`.</span></span>|  
|<span data-ttu-id="64d4f-122">nazwa</span><span class="sxs-lookup"><span data-stu-id="64d4f-122">name</span></span>|<span data-ttu-id="64d4f-123">Ciąg zawierający nazwę środowiska uruchomieniowego przepływu.</span><span class="sxs-lookup"><span data-stu-id="64d4f-123">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="64d4f-124">Nazwa jest używana w danych wyjściowych do odróżnienia to środowisko uruchomieniowe od innych środowisk uruchomieniowych, które mogą być uruchomione na komputerze, na przykład liczników wydajności.</span><span class="sxs-lookup"><span data-stu-id="64d4f-124">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="64d4f-125">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="64d4f-125">The default is an empty string.</span></span>|  
|<span data-ttu-id="64d4f-126">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="64d4f-126">validateOnCreate</span></span>|<span data-ttu-id="64d4f-127">Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi przy otwarciu WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="64d4f-127">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="64d4f-128">Jeśli ten atrybut ma wartość `true`, sprawdzanie poprawności przepływu pracy jest wykonywane zawsze `WorkflowServiceHost.Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="64d4f-128">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="64d4f-129">W przypadku znalezienia błędów sprawdzania poprawności <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , jest zgłaszany błąd.</span><span class="sxs-lookup"><span data-stu-id="64d4f-129">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="64d4f-130">Jeśli ta właściwość jest równa `false`, weryfikacja definicji przepływu pracy nie zostanie wykonana.</span><span class="sxs-lookup"><span data-stu-id="64d4f-130">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="64d4f-131">Wartość domyślna dla tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="64d4f-131">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64d4f-132">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64d4f-132">Child Elements</span></span>  
  
|<span data-ttu-id="64d4f-133">Element</span><span class="sxs-lookup"><span data-stu-id="64d4f-133">Element</span></span>|<span data-ttu-id="64d4f-134">Opis</span><span class="sxs-lookup"><span data-stu-id="64d4f-134">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="64d4f-135">commonParameters</span><span class="sxs-lookup"><span data-stu-id="64d4f-135">commonParameters</span></span>|<span data-ttu-id="64d4f-136">Kolekcja wspólnych parametrów używane przez usługi.</span><span class="sxs-lookup"><span data-stu-id="64d4f-136">A collection of common parameters used by services.</span></span> <span data-ttu-id="64d4f-137">Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.</span><span class="sxs-lookup"><span data-stu-id="64d4f-137">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="64d4f-138">usługi</span><span class="sxs-lookup"><span data-stu-id="64d4f-138">services</span></span>|<span data-ttu-id="64d4f-139">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="64d4f-139">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="64d4f-140">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="64d4f-140">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="64d4f-141">Usług określonych w kolekcji zostanie zainicjowany przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do jej usług podczas odpowiednie <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="64d4f-141">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="64d4f-142">W związku z tym usługi określona w kolekcji należy wykonać niektóre zasady dotyczące podpisy ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="64d4f-142">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="64d4f-143">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="64d4f-143">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64d4f-144">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64d4f-144">Parent Elements</span></span>  
  
|<span data-ttu-id="64d4f-145">Element</span><span class="sxs-lookup"><span data-stu-id="64d4f-145">Element</span></span>|<span data-ttu-id="64d4f-146">Opis</span><span class="sxs-lookup"><span data-stu-id="64d4f-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64d4f-147">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="64d4f-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="64d4f-148">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="64d4f-148">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64d4f-149">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64d4f-149">Remarks</span></span>  
 <span data-ttu-id="64d4f-150">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="64d4f-150">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d4f-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="64d4f-151">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="64d4f-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64d4f-152">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="64d4f-153">Pliki konfiguracji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="64d4f-153">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
