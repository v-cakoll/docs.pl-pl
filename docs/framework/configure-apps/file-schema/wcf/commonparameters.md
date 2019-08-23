---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a92a81062e92f832be78af2bfd75270390eaac3e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919493"
---
# <a name="commonparameters"></a><span data-ttu-id="e56f8-101">\<Parametry ></span><span class="sxs-lookup"><span data-stu-id="e56f8-101">\<commonParameters></span></span>
<span data-ttu-id="e56f8-102">Reprezentuje kolekcję parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="e56f8-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="e56f8-103">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="e56f8-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="e56f8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e56f8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e56f8-105">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="e56f8-105">\<behaviors></span></span>  
<span data-ttu-id="e56f8-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e56f8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e56f8-107">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="e56f8-107">\<behavior></span></span>  
<span data-ttu-id="e56f8-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="e56f8-108">\<workflowRuntime></span></span>  
<span data-ttu-id="e56f8-109">\<Parametry ></span><span class="sxs-lookup"><span data-stu-id="e56f8-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e56f8-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="e56f8-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e56f8-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e56f8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e56f8-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e56f8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e56f8-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e56f8-113">Attributes</span></span>  
 <span data-ttu-id="e56f8-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="e56f8-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e56f8-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e56f8-115">Child Elements</span></span>  
  
|<span data-ttu-id="e56f8-116">Element</span><span class="sxs-lookup"><span data-stu-id="e56f8-116">Element</span></span>|<span data-ttu-id="e56f8-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e56f8-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e56f8-118">\<add></span><span class="sxs-lookup"><span data-stu-id="e56f8-118">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="e56f8-119">Dodaje parę nazwa-wartość wspólnych parametrów używanych przez usługi do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e56f8-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e56f8-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e56f8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e56f8-121">Element</span><span class="sxs-lookup"><span data-stu-id="e56f8-121">Element</span></span>|<span data-ttu-id="e56f8-122">Opis</span><span class="sxs-lookup"><span data-stu-id="e56f8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e56f8-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="e56f8-123">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="e56f8-124">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="e56f8-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e56f8-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e56f8-125">Remarks</span></span>  
 <span data-ttu-id="e56f8-126">Element definiuje wszystkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="e56f8-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e56f8-127">Usługa śledzenia SQL nie będzie w sposób ciągły używać wartości, `ConnectionString` jeśli została określona `<commonParameters>` w sekcji.</span><span class="sxs-lookup"><span data-stu-id="e56f8-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="e56f8-128">Niektóre jego operacje, takie jak pobieranie właściwości `StateMachineWorkflowInstance.StateHistory` , mogą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e56f8-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="e56f8-129">Aby to obejść, określ `ConnectionString` atrybut w sekcji konfiguracji dla dostawcy śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e56f8-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="e56f8-130">W przypadku usług, które zatwierdzają partie pracy do magazynów <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i, można umożliwić im ponawianie transakcji `EnableRetries` przy użyciu parametru, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e56f8-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="e56f8-131">Należy zauważyć, `EnableRetries` że parametr można ustawić na poziomie globalnym (jak pokazano w sekcji *Parametry* ) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *usługi* ).</span><span class="sxs-lookup"><span data-stu-id="e56f8-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="e56f8-132">Poniższy przykładowy kod pokazuje, jak zmienić wspólne parametry programowo.</span><span class="sxs-lookup"><span data-stu-id="e56f8-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="e56f8-133">Aby uzyskać więcej informacji o korzystaniu z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e56f8-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56f8-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="e56f8-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="e56f8-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e56f8-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="e56f8-136">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e56f8-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="e56f8-137">\<add></span><span class="sxs-lookup"><span data-stu-id="e56f8-137">\<add></span></span>](add-of-commonparameters.md)
