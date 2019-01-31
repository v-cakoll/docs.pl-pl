---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 39a9c5583e5d8972dc4051a6cad13249821d8fb9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278620"
---
# <a name="commonparameters"></a><span data-ttu-id="b2d77-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="b2d77-101">\<commonParameters></span></span>
<span data-ttu-id="b2d77-102">Reprezentuje kolekcję parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="b2d77-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="b2d77-103">Ta kolekcja zwykle będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.</span><span class="sxs-lookup"><span data-stu-id="b2d77-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="b2d77-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b2d77-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b2d77-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="b2d77-105">\<behaviors></span></span>  
<span data-ttu-id="b2d77-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="b2d77-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b2d77-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="b2d77-107">\<behavior></span></span>  
<span data-ttu-id="b2d77-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="b2d77-108">\<workflowRuntime></span></span>  
<span data-ttu-id="b2d77-109">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="b2d77-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d77-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2d77-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2d77-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b2d77-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b2d77-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b2d77-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2d77-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b2d77-113">Attributes</span></span>  
 <span data-ttu-id="b2d77-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b2d77-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b2d77-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b2d77-115">Child Elements</span></span>  
  
|<span data-ttu-id="b2d77-116">Element</span><span class="sxs-lookup"><span data-stu-id="b2d77-116">Element</span></span>|<span data-ttu-id="b2d77-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b2d77-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2d77-118">\<add></span><span class="sxs-lookup"><span data-stu-id="b2d77-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="b2d77-119">Dodaje parę nazwa / wartość wspólne parametry używane przez usługi do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b2d77-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b2d77-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b2d77-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b2d77-121">Element</span><span class="sxs-lookup"><span data-stu-id="b2d77-121">Element</span></span>|<span data-ttu-id="b2d77-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b2d77-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b2d77-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="b2d77-123">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="b2d77-124">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> do hostingu opartego o przepływ pracy usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b2d77-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2d77-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2d77-125">Remarks</span></span>  
 <span data-ttu-id="b2d77-126">`<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="b2d77-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2d77-127">Usługa śledzenia programu SQL nie zawsze używa `ConnectionString` wartość, jeśli została określona w `<commonParameters>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="b2d77-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="b2d77-128">Niektóre z jego operacje, takie jak pobieranie `StateMachineWorkflowInstance.StateHistory` właściwości może się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="b2d77-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="b2d77-129">Aby obejść to, określ `ConnectionString` atrybutu w sekcji konfiguracji dla dostawcy śledzenia, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b2d77-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="b2d77-130">Dla usług, które zatwierdzenia pracy wsadów stanów trwałych magazynach, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, aby umożliwić ich ponowić próbę ich transakcji przy użyciu `EnableRetries` parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b2d77-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="b2d77-131">Należy zauważyć, że `EnableRetries` parametr może być ustawiony na poziomie globalnym (jak pokazano na *CommonParameters* sekcji) lub dla poszczególnych usług obsługujących `EnableRetries` (jak pokazano na *usług*sekcji).</span><span class="sxs-lookup"><span data-stu-id="b2d77-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="b2d77-132">Poniższy przykład kodu pokazuje, jak programowo zmienić typowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="b2d77-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="b2d77-133">Aby uzyskać więcej informacji o korzystaniu z pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b2d77-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2d77-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2d77-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="b2d77-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2d77-135">See also</span></span>
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="b2d77-136">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b2d77-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="b2d77-137">\<add></span><span class="sxs-lookup"><span data-stu-id="b2d77-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
