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
# <a name="commonparameters"></a>\<commonParameters>
Reprezentuje kolekcję parametrów, które są używane globalnie w wielu usługach. Ta kolekcja zazwyczaj będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<zachowania>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<usługiZachowady>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>zachowania**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>przepływu pracy**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<dodaj>](add-of-commonparameters.md)|Dodaje parę nazwa wartość wspólnych parametrów używanych przez usługi do kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>przepływu pracy](workflowruntime.md)|Określa ustawienia wystąpienia dla <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu usług Windows Communication Foundation (WCF) opartych na przepływie pracy.|  
  
## <a name="remarks"></a>Uwagi  
 Element `<commonParameters>` definiuje wszelkie parametry, które są używane globalnie w wielu usługach, na przykład `ConnectionString` podczas korzystania z <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
> [!NOTE]
> Usługa śledzenia SQL nie konsekwentnie `ConnectionString` używa wartości, jeśli `<commonParameters>` jest określona w sekcji. Niektóre z jego operacji, `StateMachineWorkflowInstance.StateHistory` takich jak pobieranie właściwości może zakończyć się niepowodzeniem. Aby obejść ten problem, należy określić `ConnectionString` atrybut w sekcji konfiguracji dla dostawcy śledzenia, jak wskazano w poniższym przykładzie.  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 Dla usług, które zatwierdzają partii pracy <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>do magazynów trwałości, takich jak `EnableRetries` i , można włączyć je ponowić próbę ich transakcji przy użyciu parametru, jak pokazano w poniższym przykładzie:  
  
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
  
 Należy zauważyć, `EnableRetries` że parametr można ustawić na poziomie globalnym (jak pokazano w *commonparameters* sekcji) lub dla poszczególnych usług, które obsługują `EnableRetries` (jak pokazano w sekcji *Usługi).*  
  
 Poniższy przykładowy kod pokazuje, jak programowo zmieniać typowe parametry:
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Aby uzyskać więcej informacji na temat używania <xref:System.Workflow.Runtime.WorkflowRuntime> pliku konfiguracyjnego do kontrolowania zachowania obiektu aplikacji hosta Fundacji przepływu pracy systemu Windows, zobacz [Pliki konfiguracyjne przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Przykład  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<dodaj>](add-of-commonparameters.md)
