---
title: <workflowRuntime>
ms.date: 03/30/2017
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
ms.openlocfilehash: d12656b77fa219080382603fd04a542d2fa9064a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399087"
---
# \<workflowRuntime>
<span data-ttu-id="a147b-101">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="a147b-101">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowRuntime>**  
  
## <a name="syntax"></a><span data-ttu-id="a147b-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="a147b-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a147b-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a147b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a147b-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a147b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a147b-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a147b-105">Attributes</span></span>  
  
|<span data-ttu-id="a147b-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a147b-106">Attribute</span></span>|<span data-ttu-id="a147b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a147b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a147b-108">cachedInstanceExpiration</span><span class="sxs-lookup"><span data-stu-id="a147b-108">cachedInstanceExpiration</span></span>|<span data-ttu-id="a147b-109">Opcjonalna <xref:System.TimeSpan> wartość, która określa maksymalny czas trwania wystąpienia przepływu pracy w pamięci w stanie bezczynności, zanim zostanie wymuszone zwolnione lub przerwane.</span><span class="sxs-lookup"><span data-stu-id="a147b-109">An optional <xref:System.TimeSpan> value that specifies the maximum duration a workflow instance can stay in-memory in idle state before it is forcefully unloaded or aborted.</span></span> <span data-ttu-id="a147b-110">Jeśli element WorkflowRuntime ma `PersistenceService` unloadOnIdle, ten atrybut jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="a147b-110">If the workflowruntime has `PersistenceService` which performs unloadOnIdle, this attribute is ignored.</span></span>|  
|<span data-ttu-id="a147b-111">enablePerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="a147b-111">enablePerformanceCounters</span></span>|<span data-ttu-id="a147b-112">Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone.</span><span class="sxs-lookup"><span data-stu-id="a147b-112">An optional Boolean value that specifies whether performance counters are enabled.</span></span> <span data-ttu-id="a147b-113">Liczniki wydajności dostarczają informacji na temat różnych statystyk związanych z przepływem pracy, ale powodują spadek wydajności, gdy uruchamiany jest aparat środowiska uruchomieniowego przepływu pracy i kiedy wystąpienia przepływu pracy są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="a147b-113">Performance counters provide information on various workflow-related statistics, but they cause a performance penalty when the workflow runtime engine starts, and when workflow instances are running.</span></span> <span data-ttu-id="a147b-114">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="a147b-114">The default value is `true`.</span></span>|  
|<span data-ttu-id="a147b-115">name</span><span class="sxs-lookup"><span data-stu-id="a147b-115">name</span></span>|<span data-ttu-id="a147b-116">Ciąg zawierający nazwę aparatu środowiska uruchomieniowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a147b-116">A string containing the name of the workflow runtime engine.</span></span> <span data-ttu-id="a147b-117">Nazwa jest używana w danych wyjściowych w celu odróżnienia tego środowiska uruchomieniowego od innych środowisk uruchomieniowych, które mogą być uruchomione w systemie, na przykład w licznikach wydajności.</span><span class="sxs-lookup"><span data-stu-id="a147b-117">The name is used in output to distinguish this runtime from other runtimes that may be running on the system, for example, in performance counters.</span></span><br /><br /> <span data-ttu-id="a147b-118">Wartość domyślna to pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="a147b-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="a147b-119">validateOnCreate</span><span class="sxs-lookup"><span data-stu-id="a147b-119">validateOnCreate</span></span>|<span data-ttu-id="a147b-120">Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi po otwarciu obiektu WorkflowServiceHost.</span><span class="sxs-lookup"><span data-stu-id="a147b-120">An optional Boolean value that specifies whether validation of workflow definition will occur when the WorkflowServiceHost is opened.</span></span>  <span data-ttu-id="a147b-121">Gdy ten atrybut jest ustawiony na `true` , sprawdzanie poprawności przepływu pracy jest wykonywane za każdym razem, gdy `WorkflowServiceHost.Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a147b-121">When this attribute is set to `true`, the workflow validation is executed every time `WorkflowServiceHost.Open` is called.</span></span> <span data-ttu-id="a147b-122">Jeśli zostaną znalezione błędy walidacji, <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> zostanie zgłoszony błąd.</span><span class="sxs-lookup"><span data-stu-id="a147b-122">If validation errors are found, a <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> error is thrown.</span></span><br /><br /> <span data-ttu-id="a147b-123">Gdy ta właściwość jest ustawiona na `false` , nie będzie wykonywane Walidacja definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a147b-123">When this property is set to `false`, no Workflow definition validation will happen.</span></span><br /><br /> <span data-ttu-id="a147b-124">Wartość domyślna tej właściwości to `true` .</span><span class="sxs-lookup"><span data-stu-id="a147b-124">The default value for this property is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a147b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a147b-125">Child Elements</span></span>  
  
|<span data-ttu-id="a147b-126">Element</span><span class="sxs-lookup"><span data-stu-id="a147b-126">Element</span></span>|<span data-ttu-id="a147b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="a147b-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a147b-128">commonParameters</span><span class="sxs-lookup"><span data-stu-id="a147b-128">commonParameters</span></span>|<span data-ttu-id="a147b-129">Kolekcja typowych parametrów używanych przez usługi.</span><span class="sxs-lookup"><span data-stu-id="a147b-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="a147b-130">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="a147b-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
|<span data-ttu-id="a147b-131">services</span><span class="sxs-lookup"><span data-stu-id="a147b-131">services</span></span>|<span data-ttu-id="a147b-132">Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu.</span><span class="sxs-lookup"><span data-stu-id="a147b-132">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="a147b-133">Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="a147b-133">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="a147b-134">Usługi określone w kolekcji zostaną zainicjowane przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do swoich usług, gdy <xref:System.Workflow.Runtime.WorkflowRuntime> zostanie wywołany odpowiedni Konstruktor.</span><span class="sxs-lookup"><span data-stu-id="a147b-134">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="a147b-135">W związku z tym usługi określone w kolekcji muszą przestrzegać pewnych zasad dotyczących podpisów ich konstruktorów.</span><span class="sxs-lookup"><span data-stu-id="a147b-135">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="a147b-136">Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="a147b-136">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a147b-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a147b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="a147b-138">Element</span><span class="sxs-lookup"><span data-stu-id="a147b-138">Element</span></span>|<span data-ttu-id="a147b-139">Opis</span><span class="sxs-lookup"><span data-stu-id="a147b-139">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a147b-140">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="a147b-140">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a147b-141">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a147b-141">Remarks</span></span>  
 <span data-ttu-id="a147b-142">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a147b-142">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a147b-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="a147b-143">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a147b-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a147b-144">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="a147b-145">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a147b-145">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
