---
title: <add> z <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: e0ca00911577f9f210def9326df261f772f9c26d
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674428"
---
# <a name="add-of-commonparameters"></a>\<Dodaj > z \<commonParameters >
Określa pary nazwa wartość parametrów, które są globalnie używane w wielu usługach. Zazwyczaj ten parametr zawiera parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<workflowRuntime>  
\<commonParameters>  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Nazwa parametru określonego dla usługi.|  
|value|Wartość parametru określonego dla usługi.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|Kolekcja wspólnych parametrów używane przez usługi. Ta kolekcja zwykle będzie zawierać parametry połączenia bazy danych, które mogą być współużytkowane przez trwałych usług.|  
  
## <a name="remarks"></a>Uwagi  
 `<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
 Dla usług, które zatwierdzenia pracy wsadów stanów trwałych magazynach, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, aby umożliwić ich ponowić próbę ich transakcji przy użyciu `EnableRetries` parametru, jak pokazano w poniższym przykładzie:  
  
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
  
 Należy zauważyć, że `EnableRetries` parametr może być ustawiony na poziomie globalną (jak pokazano na *CommonParameters* sekcji) lub dla poszczególnych usług obsługujących `EnableRetries` (jak pokazano na *usług*sekcji).  
  
 Aby uzyskać więcej informacji na temat korzystania z pliku konfiguracji w celu sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiekt aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).  
  
## <a name="example"></a>Przykład  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- [Pliki konfiguracji przepływu pracy](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))
- [\<commonParameters>](commonparameters.md)
