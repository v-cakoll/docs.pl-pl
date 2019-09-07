---
title: <add> dla <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400664"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="37845-102">\<Dodawanie > \<parametry ></span><span class="sxs-lookup"><span data-stu-id="37845-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="37845-103">Określa pary nazwa-wartość parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="37845-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="37845-104">Zazwyczaj ten parametr zawiera parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="37845-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="37845-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="37845-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37845-106">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="37845-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="37845-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowań**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37845-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="37845-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> serviceBehaviors**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37845-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="37845-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zachowania**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="37845-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="37845-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="37845-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="37845-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Parametry >** ](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="37845-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="37845-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Dodaj >**</span><span class="sxs-lookup"><span data-stu-id="37845-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37845-113">Składnia</span><span class="sxs-lookup"><span data-stu-id="37845-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37845-114">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="37845-114">Attributes and Elements</span></span>  
 <span data-ttu-id="37845-115">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="37845-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37845-116">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="37845-116">Attributes</span></span>  
  
|<span data-ttu-id="37845-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="37845-117">Attribute</span></span>|<span data-ttu-id="37845-118">Opis</span><span class="sxs-lookup"><span data-stu-id="37845-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37845-119">nazwa</span><span class="sxs-lookup"><span data-stu-id="37845-119">name</span></span>|<span data-ttu-id="37845-120">Nazwa parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="37845-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="37845-121">value</span><span class="sxs-lookup"><span data-stu-id="37845-121">value</span></span>|<span data-ttu-id="37845-122">Wartość parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="37845-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37845-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="37845-123">Child Elements</span></span>  
 <span data-ttu-id="37845-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="37845-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37845-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="37845-125">Parent Elements</span></span>  
  
|<span data-ttu-id="37845-126">Element</span><span class="sxs-lookup"><span data-stu-id="37845-126">Element</span></span>|<span data-ttu-id="37845-127">Opis</span><span class="sxs-lookup"><span data-stu-id="37845-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37845-128">\<Parametry ></span><span class="sxs-lookup"><span data-stu-id="37845-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="37845-129">Kolekcja typowych parametrów używanych przez usługi.</span><span class="sxs-lookup"><span data-stu-id="37845-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="37845-130">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="37845-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37845-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37845-131">Remarks</span></span>  
 <span data-ttu-id="37845-132">Element definiuje wszystkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>. `<commonParameters>`</span><span class="sxs-lookup"><span data-stu-id="37845-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="37845-133">W przypadku usług, które zatwierdzają partie pracy do magazynów <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i, można umożliwić im ponawianie transakcji `EnableRetries` przy użyciu parametru, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="37845-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="37845-134">Należy zauważyć, `EnableRetries` że parametr można ustawić na poziomie globalnym (jak pokazano w sekcji *Parametry* ) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *usługi* ).</span><span class="sxs-lookup"><span data-stu-id="37845-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="37845-135">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="37845-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37845-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="37845-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="37845-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37845-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="37845-138">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="37845-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="37845-139">\<Parametry ></span><span class="sxs-lookup"><span data-stu-id="37845-139">\<commonParameters></span></span>](commonparameters.md)
