---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 6f187e9cdcabc358ee69d65e392bc59aa38e52ca
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398178"
---
# <a name="commonparameters"></a><span data-ttu-id="41526-101">\<Parametry ></span><span class="sxs-lookup"><span data-stu-id="41526-101">\<commonParameters></span></span>
<span data-ttu-id="41526-102">Reprezentuje kolekcję parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="41526-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="41526-103">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="41526-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="41526-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="41526-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="41526-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="41526-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="41526-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41526-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="41526-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41526-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="41526-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="41526-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="41526-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="41526-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="41526-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Parametry >**</span><span class="sxs-lookup"><span data-stu-id="41526-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41526-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="41526-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41526-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="41526-112">Attributes and Elements</span></span>  
 <span data-ttu-id="41526-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="41526-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41526-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="41526-114">Attributes</span></span>  
 <span data-ttu-id="41526-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="41526-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41526-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="41526-116">Child Elements</span></span>  
  
|<span data-ttu-id="41526-117">Element</span><span class="sxs-lookup"><span data-stu-id="41526-117">Element</span></span>|<span data-ttu-id="41526-118">Opis</span><span class="sxs-lookup"><span data-stu-id="41526-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41526-119">\<add></span><span class="sxs-lookup"><span data-stu-id="41526-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="41526-120">Dodaje parę nazwa-wartość wspólnych parametrów używanych przez usługi do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="41526-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41526-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="41526-121">Parent Elements</span></span>  
  
|<span data-ttu-id="41526-122">Element</span><span class="sxs-lookup"><span data-stu-id="41526-122">Element</span></span>|<span data-ttu-id="41526-123">Opis</span><span class="sxs-lookup"><span data-stu-id="41526-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41526-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="41526-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="41526-125">Określa ustawienia dla wystąpienia programu <xref:System.Workflow.Runtime.WorkflowRuntime> do hostowania usług Windows Communication Foundation opartych na przepływie pracy (WCF).</span><span class="sxs-lookup"><span data-stu-id="41526-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41526-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41526-126">Remarks</span></span>  
 <span data-ttu-id="41526-127">Element definiuje wszystkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="41526-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41526-128">Usługa śledzenia SQL nie będzie w sposób ciągły używać wartości, `ConnectionString` jeśli została określona `<commonParameters>` w sekcji.</span><span class="sxs-lookup"><span data-stu-id="41526-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="41526-129">Niektóre jego operacje, takie jak pobieranie właściwości `StateMachineWorkflowInstance.StateHistory` , mogą zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="41526-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="41526-130">Aby to obejść, określ `ConnectionString` atrybut w sekcji konfiguracji dla dostawcy śledzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="41526-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="41526-131">W przypadku usług, które zatwierdzają partie pracy do magazynów <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i, można umożliwić im ponawianie transakcji `EnableRetries` przy użyciu parametru, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41526-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="41526-132">Należy zauważyć, `EnableRetries` że parametr można ustawić na poziomie globalnym (jak pokazano w sekcji *Parametry* ) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *usługi* ).</span><span class="sxs-lookup"><span data-stu-id="41526-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="41526-133">Poniższy przykładowy kod pokazuje, jak zmienić wspólne parametry programowo.</span><span class="sxs-lookup"><span data-stu-id="41526-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="41526-134">Aby uzyskać więcej informacji o korzystaniu z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="41526-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41526-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="41526-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="41526-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41526-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="41526-137">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="41526-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="41526-138">\<add></span><span class="sxs-lookup"><span data-stu-id="41526-138">\<add></span></span>](add-of-commonparameters.md)
