---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153025"
---
# <a name="commonparameters"></a><span data-ttu-id="05a2f-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="05a2f-101">\<commonParameters></span></span>
<span data-ttu-id="05a2f-102">Reprezentuje kolekcję parametrów, które są używane globalnie w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="05a2f-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="05a2f-103">Ta kolekcja zazwyczaj będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.</span><span class="sxs-lookup"><span data-stu-id="05a2f-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="05a2f-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="05a2f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="05a2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="05a2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="05a2f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="05a2f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="05a2f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="05a2f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span><span class="sxs-lookup"><span data-stu-id="05a2f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05a2f-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="05a2f-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05a2f-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05a2f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="05a2f-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05a2f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05a2f-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05a2f-114">Attributes</span></span>  
 <span data-ttu-id="05a2f-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="05a2f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05a2f-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05a2f-116">Child Elements</span></span>  
  
|<span data-ttu-id="05a2f-117">Element</span><span class="sxs-lookup"><span data-stu-id="05a2f-117">Element</span></span>|<span data-ttu-id="05a2f-118">Opis</span><span class="sxs-lookup"><span data-stu-id="05a2f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05a2f-119">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="05a2f-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="05a2f-120">Dodaje parę nazwa wartość wspólnych parametrów używanych przez usługi do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="05a2f-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05a2f-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05a2f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05a2f-122">Element</span><span class="sxs-lookup"><span data-stu-id="05a2f-122">Element</span></span>|<span data-ttu-id="05a2f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="05a2f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05a2f-124">\<>przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="05a2f-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="05a2f-125">Określa ustawienia wystąpienia dla <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu usług Windows Communication Foundation (WCF) opartych na przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="05a2f-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05a2f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05a2f-126">Remarks</span></span>  
 <span data-ttu-id="05a2f-127">Element `<commonParameters>` definiuje wszelkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="05a2f-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05a2f-128">Usługa śledzenia SQL nie konsekwentnie `ConnectionString` używa wartości, jeśli `<commonParameters>` jest określona w sekcji.</span><span class="sxs-lookup"><span data-stu-id="05a2f-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="05a2f-129">Niektóre z jego operacji, `StateMachineWorkflowInstance.StateHistory` takich jak pobieranie właściwości może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="05a2f-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="05a2f-130">Aby obejść ten problem, należy określić `ConnectionString` atrybut w sekcji konfiguracji dla dostawcy śledzenia, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05a2f-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="05a2f-131">Dla usług, które zatwierdzają partii pracy <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>do magazynów trwałości, takich jak `EnableRetries` i , można włączyć je ponowić próbę ich transakcji przy użyciu parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="05a2f-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="05a2f-132">Należy zauważyć, `EnableRetries` że parametr można ustawić na poziomie globalnym (jak pokazano w *commonparameters* sekcji) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *Usługi).*</span><span class="sxs-lookup"><span data-stu-id="05a2f-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="05a2f-133">Poniższy przykładowy kod pokazuje, jak programowo zmieniać typowe parametry:</span><span class="sxs-lookup"><span data-stu-id="05a2f-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="05a2f-134">Aby uzyskać więcej informacji na temat używania <xref:System.Workflow.Runtime.WorkflowRuntime> pliku konfiguracyjnego do kontrolowania zachowania obiektu aplikacji hosta Fundacji przepływu pracy systemu Windows, zobacz [Pliki konfiguracyjne przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="05a2f-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05a2f-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="05a2f-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="05a2f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05a2f-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="05a2f-137">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="05a2f-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="05a2f-138">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="05a2f-138">\<add></span></span>](add-of-commonparameters.md)
