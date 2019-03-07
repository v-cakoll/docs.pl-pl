---
title: 'Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 4f4bcd06067775c6f43063ebe5682730deba1d4f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498890"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a>Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy

W tym temacie opisano sposób konfigurowania funkcji Store wystąpienia przepływu pracy SQL Włączanie stanów trwałych dla przepływów pracy i usługi przepływu pracy, zarówno programowo i za pomocą pliku konfiguracji.

Windows Server AppFabric upraszcza proces konfigurowania trwałości. Aby uzyskać więcej informacji, zobacz [konfiguracji trwałości sieci szkieletowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=201204)

Przed użyciem funkcji Store wystąpienia przepływu pracy SQL, należy utworzyć bazy danych, która korzysta z tej funkcji można utrwalić wystąpienia przepływu pracy. [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Konfiguracji jest kopiowana skojarzonego z funkcją Store wystąpienia przepływu pracy SQL do folderu %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN pliki skryptu SQL. Uruchom te pliki skryptów względem bazy danych programu SQL Server 2005 lub SQL Server 2008 mają Store wystąpienia przepływu pracy SQL, można użyć, aby utrwalić wystąpienia przepływu pracy. Uruchom plik SqlWorkflowInstanceStoreSchema.sql najpierw, a następnie uruchom plik SqlWorkflowInstanceStoreLogic.sql.

> [!NOTE]
> Aby wyczyścić trwałości bazy danych do nowej bazy danych, uruchom skrypty w %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN w następującej kolejności.
>
> 1. SqlWorkflowInstanceStoreSchema.sql
> 2. SqlWorkflowInstanceStoreLogic.sql

> [!IMPORTANT]
> Jeśli nie utworzysz bazę danych trwałości, funkcja Store wystąpienia przepływu pracy SQL zgłasza wyjątek podobny do następującego, gdy host próbuje zachować przepływów pracy.
>
> System.Data.SqlClient.SqlException: Nie można odnaleźć procedury składowanej "System.Activities.DurableInstancing.CreateLockOwner"

Poniżej opisano sposób włączania stanów trwałych dla przepływów pracy i usług przepływu pracy przy użyciu Store wystąpienia przepływu pracy SQL. Aby uzyskać więcej informacji na temat właściwości Store wystąpienia przepływu pracy SQL, zobacz [właściwości programu SQL przepływu pracy wystąpienie Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a>Włączanie stanów trwałych dla przepływów pracy z produktem, używanego przez WorkflowApplication

Możesz włączyć trwałość Self-Hosted przepływach pracy korzystających <xref:System.Activities.WorkflowApplication> programowo przy użyciu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> modelu obiektów. Poniższa procedura zawiera kroki, aby to zrobić.

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a>Aby włączyć opcję trwałości Self-Hosted przepływów pracy

1. Dodaj odwołanie do System.Activities.DurableInstancing.dll.

2. Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejących instrukcjach "za pomocą".

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. Konstruowania <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> i przypisz ją do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak pokazano w poniższym przykładzie kodu.

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być inny.

4. Wywoływanie <xref:System.Activities.WorkflowApplication.Persist%2A> metody <xref:System.Activities.WorkflowApplication> obiektu, aby utrwalić przepływu pracy, lub <xref:System.Activities.WorkflowApplication.Unload%2A> metodę, aby utrwalić i zwalnianie przepływu pracy. Może również obsługiwać <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzenia wygenerowane przez <xref:System.Activities.WorkflowApplication> obiektu i zwraca odpowiednią (<xref:System.Activities.PersistableIdleAction.Persist> lub <xref:System.Activities.PersistableIdleAction.Unload>) członkiem <xref:System.Activities.PersistableIdleAction>.

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> Zobacz [jak: Tworzenie i uruchamianie długiego uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kroku [Samouczek wprowadzający](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) instrukcje krok po kroku.

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a>Włączanie stanów trwałych dla produktu usług przepływu pracy, które korzystają WorkflowServiceHost

Możesz włączyć trwałość dla usługi samodzielnie hostowanej przepływu pracy, które korzystają z <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy lub <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> klasy.

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a>Używanie klasy SqlWorkflowInstanceStoreBehavior

Poniższa procedura zawiera kroki, aby użyć <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy, aby włączyć opcję trwałości dla usługi samodzielnie hostowanej przepływu pracy.

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a>Aby włączyć opcję trwałości za pomocą SqlWorkflowInstanceStoreBehavior

1. Dodaj odwołanie do System.ServiceModel.dll.

2. Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejących instrukcjach "za pomocą".

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. Utwórz wystąpienie obiektu `WorkflowServiceHost` i dodać punkty końcowe usługi przepływu pracy.

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. Konstruowania `SqlWorkflowInstanceStoreBehavior` obiektu i ustawienie właściwości obiektu zachowanie.

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. Otwórz hosta usługi przepływu pracy.

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a>Przy użyciu właściwości DurableInstancingOptions

Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiona na `SqlWorkflowInstanceStore` obiekt utworzony przy użyciu wartości konfiguracji. Dzieje się tak samo, programowo, aby ustawić <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> właściwość `WorkflowServiceHost` bez użycia `SqlWorkflowInstanceStoreBehavior` klasy, jak pokazano w poniższym przykładzie kodu.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a>Włączanie stanów trwałych dla WAS-Hosted usług przepływu pracy, które korzystają WorkflowServiceHost przy użyciu pliku konfiguracji

Możesz włączyć trwałość usługi samodzielnie hostowanej lub hostowany Windows Process Activation Service WAS przepływu pracy przy użyciu pliku konfiguracji. Usługa hostowana WAS przepływ pracy używa WorkflowServiceHost w usługach samodzielnie hostowanej przepływu pracy.

`SqlWorkflowInstanceStoreBehavior`, Zachowanie usługi, które umożliwia zmianę wygodnie [Store wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) właściwości za pomocą konfiguracji XML. Hostowana WAS usług przepływu pracy można użyć w pliku Web.config. W poniższym przykładzie konfiguracji przedstawia sposób konfigurowania Store wystąpienia przepływu pracy SQL przy użyciu `sqlWorkflowInstanceStore` zachowania elementu w pliku konfiguracji.

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

Jeśli nie ustawisz wartości `connectionString` lub `connectionStringName` właściwości Store wystąpienia przepływu pracy SQL korzysta z domyślnego o nazwie parametry połączenia `DefaultSqlWorkflowInstanceStoreConnectionString`.

Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiona na `SqlWorkflowInstanceStore` obiekt utworzony przy użyciu wartości konfiguracji. Dzieje się tak samo, programowo, aby użyć `SqlWorkflowInstanceStore` z `WorkflowServiceHost` bez użycia elementu zachowania usługi.

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> Zaleca się, że poufne informacje, takie jak nazwy użytkowników i hasła nie są przechowywane w pliku Web.config. Jeśli w pliku Web.config są przechowywane poufne informacje, należy zabezpieczyć dostęp do pliku Web.config przy użyciu systemu plików list kontroli dostępu (ACL). Ponadto można także zabezpieczyć wartości konfiguracji w pliku konfiguracji zgodnie z opisem w [szyfrowania informacji przy użyciu chronione Konfiguracja](https://go.microsoft.com/fwlink/?LinkId=178419).

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a>Machine.config elementów powiązanych z tą funkcją Store wystąpienia przepływu pracy SQL

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalacja dodaje następujące elementy związane z funkcją Store wystąpienia przepływu pracy SQL do pliku Machine.config:

- Dodaje do pliku Machine.config następujący element rozszerzenia zachowania, tak, aby można było używać \<sqlWorkflowInstanceStore > element zachowanie usługi, w pliku konfiguracyjnym Konfigurowanie trwałości dla usługi.

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
