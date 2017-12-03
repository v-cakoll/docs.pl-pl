---
title: '&lt;Parametry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbb67714a58df0c5ccec86c7eac85a5194d780a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonparametersgt"></a>&lt;Parametry&gt;
Reprezentuje kolekcję parametrów, które są globalnie używane w wielu usługach. Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<Obiekt workflowRuntime >  
\<commonParameters >  
  
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
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|Dodaje pary nazwa wartość wspólnych parametrów używane przez usługi do kolekcji.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Obiekt workflowRuntime >](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu opartego o przepływ pracy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.|  
  
## <a name="remarks"></a>Uwagi  
 `<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.  
  
> [!NOTE]
>  Usługa śledzenia programu SQL nie zawsze używa `ConnectionString` wartość, jeśli został określony w `<commonParameters>` sekcji. Niektóre z jego operacji, takich jak pobieranie `StateMachineWorkflowInstance.StateHistory` właściwości może się nie powieść. Aby obejść, określ `ConnectionString` atrybutu w sekcji konfiguracji dla dostawcy śledzenia, jak wskazano w poniższym przykładzie.  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
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
  
 Zwróć uwagę, że `EnableRetries` parametr może być ustawiony na poziomie globalnym (jak pokazano w *CommonParameters* sekcji) lub dla poszczególnych usług obsługujące `EnableRetries` (jak pokazano w *usług*sekcji).  
  
 Następujący przykładowy kod przedstawia sposób programowo zmienić typowych parametrów.  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 Aby uzyskać więcej informacji o używaniu plik konfiguracji do kontrolowania zachowania <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
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
 [Pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [\<Dodaj >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
