---
title: 'Porady: Włącz trwałość SQL dla przepływów pracy i usług przepływu pracy'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d687c00edd9d495f3b7715474d7eb2e107c23f0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Porady: Włącz trwałość SQL dla przepływów pracy i usług przepływu pracy
W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpienia przepływu pracy SQL do włączenia trwałości dla przepływów pracy i przepływ pracy usługi programowo i za pomocą pliku konfiguracji.  
  
 Windows Server AppFabric upraszcza proces konfigurowania trwałości. Aby uzyskać więcej informacji, zobacz [aplikacji sieci szkieletowej trwałości konfiguracji](http://go.microsoft.com/fwlink/?LinkId=201204)  
  
 Przed użyciem funkcji magazynu wystąpienia przepływu pracy SQL, należy utworzyć bazę danych, która używa funkcji, aby utrwalić wystąpienia przepływu pracy. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Konfiguracji jest kopiowana skojarzony z funkcją magazynu wystąpienia przepływu pracy SQL do folderu %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN plików skryptów SQL. Uruchom te pliki skryptów na bazie danych programu SQL Server 2005 lub SQL Server 2008, które mają w magazynie wystąpień przepływu pracy SQL do użycia, aby utrwalić wystąpienia przepływu pracy. Uruchom plik SqlWorkflowInstanceStoreSchema.sql najpierw, a następnie uruchom plik SqlWorkflowInstanceStoreLogic.sql.  
  
> [!NOTE]
>  Aby wyczyścić trwałości bazy danych ma nową bazą danych, należy uruchomić skrypty w %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN w następującej kolejności.  
>   
>  1.  SqlWorkflowInstanceStoreSchema.sql  
> 2.  SqlWorkflowInstanceStoreLogic.sql  
  
> [!IMPORTANT]
>  Jeśli nie utworzysz bazę danych trwałości, funkcję Magazyn wystąpienia przepływu pracy SQL zgłasza wyjątek podobny do następującego hosta próba utrwalić przepływów pracy.  
>   
>  System.Data.SqlClient.SqlException: Nie można odnaleźć procedury składowanej "System.Activities.DurableInstancing.CreateLockOwner"  
  
 W poniższych sekcjach opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy przy użyciu magazynu wystąpienia przepływu pracy SQL. [!INCLUDE[crabout](../../../includes/crabout-md.md)] właściwości magazynu wystąpienia przepływu pracy SQL, zobacz [właściwości z przepływu pracy wystąpienia magazynu SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Włączenie trwałości dla przepływów pracy Self-Hosted, używanego przez obiekt WorkflowApplication  
 Można włączyć trwałości dla siebie przepływy pracy używające <xref:System.Activities.WorkflowApplication> programowo przy użyciu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> obiektu modelu. Poniższa procedura zawiera kroki, aby to zrobić.  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Aby włączyć trwałości dla siebie przepływów pracy  
  
1.  Dodaj odwołanie do System.Activites.DurableInstancing.dll.  
  
2.  Dodaj następującą instrukcję na początku pliku źródłowego po istniejących instrukcji "using".  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  Utworzyć <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> i przypisz go do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak pokazano w poniższym przykładzie kodu.  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być różne.  
  
4.  Wywołanie <xref:System.Activities.WorkflowApplication.Persist%2A> metoda <xref:System.Activities.WorkflowApplication> obiekt, aby utrwalić przepływu pracy, lub <xref:System.Activities.WorkflowApplication.Unload%2A> metodę, aby utrwalić i zwolnić przepływu pracy. Można również obsługiwać <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzenie zgłaszane przez <xref:System.Activities.WorkflowApplication> obiektu i zwraca odpowiednie (<xref:System.Activities.PersistableIdleAction.Persist> lub <xref:System.Activities.PersistableIdleAction.Unload>) członek <xref:System.Activities.PersistableIdleAction>.  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  Zobacz [utrwalanie aplikacji przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) na przykład [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) przykład włączenie trwałości dla przepływów pracy za pomocą <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>i [porady: tworzenie i uruchamianie długi Uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kroku [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) instrukcje krok po kroku.  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Włączenie trwałości dla usługi przepływu pracy Self-Hosted używanego WorkflowServiceHost  
 Można włączyć trwałości dla usług hostowania samoobsługowego przepływu pracy, które używają <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy lub <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> klasy.  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Za pomocą klasy SqlWorkflowInstanceStoreBehavior  
 Poniższa procedura zawiera kroki, aby użyć <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy w celu włączenia trwałości dla usługi hostowanej własnym przepływu pracy.  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Aby umożliwić utrwalenie za pomocą SqlWorkflowInstanceStoreBehavior  
  
1.  Dodaj odwołanie do System.ServiceModel.dll.  
  
2.  Dodaj następującą instrukcję na początku pliku źródłowego po istniejących instrukcji "using".  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  Utwórz wystąpienie `WorkflowServiceHost` i dodać punkty końcowe usługi przepływu pracy.  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  Utworzyć `SqlWorkflowInstanceStoreBehavior` obiektu i można ustawić właściwości obiektu zachowanie.  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  Otworzyć hosta usługi przepływu pracy.  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  Zobacz [wbudowanych konfiguracji](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) na przykład [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) przykład włączenie trwałości dla usługi przepływu pracy przy użyciu `SqlWorkflowInstanceStoreBehavior` klasy.  
  
### <a name="using-the-durableinstancingoptions-property"></a>Za pomocą właściwości DurableInstancingOptions  
 Gdy `SqlWorkflowInstanceStoreBehavior` zostanie zastosowana, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` ma ustawioną wartość `SqlWorkflowInstanceStore` obiektów utworzonych przy użyciu wartości konfiguracji. Należy je programowo, aby ustawić <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> właściwość `WorkflowServiceHost` bez użycia `SqlWorkflowInstanceStoreBehavior` klasy, jak pokazano w poniższym przykładzie kodu.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Włączenie trwałości dla usługi przepływu pracy WAS-Hosted używanego WorkflowServiceHost przy użyciu pliku konfiguracji  
 W przypadku włączenia trwałości dla usług hostowania samoobsługowego lub hostowana usługa aktywacji procesów systemu Windows WAS przepływu pracy, przy użyciu pliku konfiguracji. Usługa hostowana usługa WAS przepływ pracy używa WorkflowServiceHost jak usług hostowania samoobsługowego przepływu pracy.  
  
 `SqlWorkflowInstanceStoreBehavior`, Zachowanie usługi, która pozwala łatwo zmienić [magazyn wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) właściwości za pośrednictwem pliku XML konfiguracji. Dla usługi hostowanej WAS przepływu pracy Użyj pliku Web.config. W poniższym przykładzie konfiguracji pokazano, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu `sqlWorkflowInstanceStore` zachowanie elementu w pliku konfiguracji.  
  
```xml  
<serviceBehaviors>  
    <behavior name="">  
        <sqlWorkflowInstanceStore   
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                    instanceEncodingOption="GZip | None"  
                    instanceCompletionAction="DeleteAll | DeleteNothing"  
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"  
                    hostLockRenewalPeriod="00:00:30"   
                    runnableInstancesDetectionPeriod="00:00:05">  
  
        <sqlWorkflowInstanceStore/>  
    </behavior>  
</serviceBehaviors>  
```  
  
 Jeśli nie należy ustawiać wartości `connectionString` lub `connectionStringName` właściwość, w magazynie wystąpień przepływu pracy SQL używa domyślnie nazwane parametry połączenia `DefaultSqlWorkflowInstanceStoreConnectionString`.  
  
 Gdy `SqlWorkflowInstanceStoreBehavior` zostanie zastosowana, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` ma ustawioną wartość `SqlWorkflowInstanceStore` obiektów utworzonych przy użyciu wartości konfiguracji. Należy je programowo, aby użyć `SqlWorkflowInstanceStore` z `WorkflowServiceHost` bez za pomocą elementu zachowania usługi.  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  Zaleca się, że poufne informacje, takie jak nazwy użytkowników i hasła nie są przechowywane w pliku Web.config. Jeśli w pliku Web.config są przechowywane poufne informacje, należy zabezpieczyć dostęp do pliku Web.config przy użyciu list kontroli dostępu (ACL) w systemie plików. Ponadto można także zabezpieczyć wartości konfiguracji w pliku konfiguracji jak wspomniano w [szyfrowania informacji przy użyciu chronione Konfiguracja](http://go.microsoft.com/fwlink/?LinkId=178419).  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Elementy Machine.config powiązanych z tą funkcją magazynu wystąpienia przepływu pracy SQL  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalacji doda następujące elementy związane z funkcji magazynu wystąpienia przepływu pracy SQL w pliku Machine.config:  
  
-   Dodaje następujący element rozszerzenia zachowania do pliku Machine.config, dzięki czemu można używać <`sqlWorkflowInstanceStore`> Usługa zachowanie elementu w pliku konfiguracyjnym Konfigurowanie trwałości dla usługi.  
  
    ```xml  
    <configuration>  
        <system.serviceModel>  
            <extensions>  
                <behaviorExtensions>  
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
                </behaviorExtensions>  
            </extensions>  
        <system.serviceModel>  
    <configuration>  
    ```
