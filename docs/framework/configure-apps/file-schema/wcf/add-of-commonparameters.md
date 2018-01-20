---
title: '&lt;add&gt; w &lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef23ba0fa39b01a7cf55c8b2b6cb0beb20be8631
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a>&lt;add&gt; w &lt;commonParameters&gt;
Określa pary nazwa wartość parametrów, które są globalnie używane w wielu usługach. Zazwyczaj ten parametr zawiera parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<behavior>  
\<workflowRuntime>  
\<commonParameters >  
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
|[\<commonParameters>](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|Kolekcja wspólnych parametrów używane przez usługi. Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.|  
  
## <a name="remarks"></a>Uwagi  
 `<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
 Dla usług, które zatwierdzania pracy wsadów magazynów trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, można włączyć je ponowić próbę ich transakcji przy użyciu `EnableRetries` parametru, jak pokazano w poniższym przykładzie:  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 Zwróć uwagę, że `EnableRetries` parametru można ustawić albo globalną (jak pokazano w *CommonParameters* sekcji) lub dla poszczególnych usług obsługujące `EnableRetries` (jak pokazano w *usług*sekcji).  
  
 Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
## <a name="example"></a>Przykład  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [Pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [\<commonParameters>](http://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
