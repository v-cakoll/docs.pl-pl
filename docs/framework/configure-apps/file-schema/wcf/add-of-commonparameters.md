---
title: <add> dla <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400664"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="7342b-102">\<add> dla \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="7342b-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="7342b-103">Określa pary nazwa-wartość parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="7342b-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="7342b-104">Zazwyczaj ten parametr zawiera parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="7342b-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7342b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7342b-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7342b-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7342b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7342b-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7342b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7342b-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7342b-108">Attributes</span></span>  
  
|<span data-ttu-id="7342b-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7342b-109">Attribute</span></span>|<span data-ttu-id="7342b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7342b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7342b-111">name</span><span class="sxs-lookup"><span data-stu-id="7342b-111">name</span></span>|<span data-ttu-id="7342b-112">Nazwa parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="7342b-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="7342b-113">value</span><span class="sxs-lookup"><span data-stu-id="7342b-113">value</span></span>|<span data-ttu-id="7342b-114">Wartość parametru określonego dla usługi.</span><span class="sxs-lookup"><span data-stu-id="7342b-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7342b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7342b-115">Child Elements</span></span>  
 <span data-ttu-id="7342b-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="7342b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7342b-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7342b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7342b-118">Element</span><span class="sxs-lookup"><span data-stu-id="7342b-118">Element</span></span>|<span data-ttu-id="7342b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="7342b-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="7342b-120">Kolekcja typowych parametrów używanych przez usługi.</span><span class="sxs-lookup"><span data-stu-id="7342b-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="7342b-121">Ta kolekcja zazwyczaj obejmuje parametry połączenia z bazą danych, które mogą być współużytkowane przez trwałe usługi.</span><span class="sxs-lookup"><span data-stu-id="7342b-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7342b-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7342b-122">Remarks</span></span>  
 <span data-ttu-id="7342b-123">`<commonParameters>`Element definiuje wszystkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="7342b-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="7342b-124">W przypadku usług, które zatwierdzają partie pracy do magazynów trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , można umożliwić im ponawianie transakcji przy użyciu `EnableRetries` parametru, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7342b-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="7342b-125">Należy zauważyć, że `EnableRetries` parametr można ustawić na poziomie globalnym (jak pokazano w sekcji *Parametry* ) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *usługi* ).</span><span class="sxs-lookup"><span data-stu-id="7342b-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="7342b-126">Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu Windows Workflow Foundation aplikacji hosta, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7342b-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7342b-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="7342b-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="7342b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7342b-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="7342b-129">[Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7342b-129">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
