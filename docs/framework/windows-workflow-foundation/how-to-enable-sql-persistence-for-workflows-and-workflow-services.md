---
title: 'Instrukcje: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 4dc5648d748372828c5b9a36441bfb02eef045e1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460877"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="086a8-102">Instrukcje: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="086a8-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="086a8-103">W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpień przepływu pracy SQL w celu zapewnienia trwałości dla przepływów pracy i usług przepływu pracy w sposób programistyczny i przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="086a8-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="086a8-104">Sieć szkieletowa aplikacji systemu Windows Server upraszcza proces konfigurowania trwałości.</span><span class="sxs-lookup"><span data-stu-id="086a8-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="086a8-105">Aby uzyskać więcej informacji, zobacz [Konfiguracja trwałości usługi App Fabric](https://go.microsoft.com/fwlink/?LinkId=201204).</span><span class="sxs-lookup"><span data-stu-id="086a8-105">For more information, see [App Fabric Persistence Configuration](https://go.microsoft.com/fwlink/?LinkId=201204).</span></span>

<span data-ttu-id="086a8-106">Przed użyciem funkcji magazynu wystąpień przepływu pracy SQL Utwórz bazę danych używaną przez funkcję do utrwalania wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="086a8-107">Program konfiguracji [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] kopiuje pliki skryptów SQL skojarzonych z funkcją Magazyn wystąpień przepływu pracy SQL do folderu%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN.</span><span class="sxs-lookup"><span data-stu-id="086a8-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="086a8-108">Uruchom te pliki skryptów dla bazy danych SQL Server 2005 lub SQL Server 2008, która ma być używana przez magazyn wystąpień programu SQL do utrwalania wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="086a8-109">Najpierw uruchom plik SqlWorkflowInstanceStoreSchema. SQL, a następnie uruchom plik SqlWorkflowInstanceStoreLogic. SQL.</span><span class="sxs-lookup"><span data-stu-id="086a8-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="086a8-110">Aby wyczyścić bazę danych trwałości w celu utworzenia nowej bazy danych, Uruchom skrypty w%WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN w następującej kolejności.</span><span class="sxs-lookup"><span data-stu-id="086a8-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="086a8-111">SqlWorkflowInstanceStoreSchema. SQL</span><span class="sxs-lookup"><span data-stu-id="086a8-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="086a8-112">SqlWorkflowInstanceStoreLogic. SQL</span><span class="sxs-lookup"><span data-stu-id="086a8-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="086a8-113">Jeśli nie utworzysz bazy danych trwałości, funkcja magazynu wystąpień przepływu pracy SQL zgłasza wyjątek podobny do poniższego, gdy host próbuje utrwalać przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="086a8-114">System. Data. SqlClient. SqlException: nie można znaleźć procedury składowanej "System. Activities. DurableInstancing. CreateLockOwner"</span><span class="sxs-lookup"><span data-stu-id="086a8-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="086a8-115">W poniższych sekcjach opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy w programie SQL Server.</span><span class="sxs-lookup"><span data-stu-id="086a8-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="086a8-116">Aby uzyskać więcej informacji na temat właściwości magazynu wystąpień przepływu pracy SQL, zobacz [właściwości magazynu wystąpień przepływu pracy SQL](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="086a8-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="086a8-117">Włączanie trwałości dla samohostowanych przepływów pracy korzystających z funkcji WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="086a8-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="086a8-118">Można włączyć trwałość dla samodzielnych przepływów pracy, które wykorzystują <xref:System.Activities.WorkflowApplication> programowo przy użyciu modelu obiektów <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>.</span><span class="sxs-lookup"><span data-stu-id="086a8-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="086a8-119">Poniższa procedura zawiera kroki, które należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="086a8-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="086a8-120">Aby włączyć trwałość dla samodzielnych przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="086a8-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="086a8-121">Dodaj odwołanie do elementu System. Activities. DurableInstancing. dll.</span><span class="sxs-lookup"><span data-stu-id="086a8-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="086a8-122">Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejącej instrukcji "Using".</span><span class="sxs-lookup"><span data-stu-id="086a8-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="086a8-123">Utwórz <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> i przypisz go do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> <xref:System.Activities.WorkflowApplication>, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="086a8-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="086a8-124">W zależności od wersji SQL Server Nazwa serwera parametrów połączenia może się różnić.</span><span class="sxs-lookup"><span data-stu-id="086a8-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="086a8-125">Wywołaj metodę <xref:System.Activities.WorkflowApplication.Persist%2A> na obiekcie <xref:System.Activities.WorkflowApplication>, aby zachować przepływ pracy lub <xref:System.Activities.WorkflowApplication.Unload%2A> metodę utrwalania i zwalniania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="086a8-126">Można także obsłużyć zdarzenie <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zgłoszone przez obiekt <xref:System.Activities.WorkflowApplication> i zwrócić odpowiedni element członkowski (<xref:System.Activities.PersistableIdleAction.Persist> lub <xref:System.Activities.PersistableIdleAction.Unload>) <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="086a8-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="086a8-127">Aby uzyskać instrukcje krok po kroku, zobacz artykuł [jak utworzyć i uruchomić długotrwały przepływ pracy](how-to-create-and-run-a-long-running-workflow.md) w [samouczku wprowadzenie](getting-started-tutorial.md) .</span><span class="sxs-lookup"><span data-stu-id="086a8-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="086a8-128">Włączanie trwałości dla samodzielnych usług przepływu pracy korzystających z obiektu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="086a8-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="086a8-129">Można włączyć trwałość dla samodzielnych usług przepływu pracy, które używają <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu klasy <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> lub klasy <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>.</span><span class="sxs-lookup"><span data-stu-id="086a8-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="086a8-130">Korzystanie z klasy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="086a8-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="086a8-131">Poniższa procedura zawiera kroki umożliwiające użycie klasy <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> w celu zapewnienia trwałości dla samodzielnych usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="086a8-132">Aby włączyć trwałość przy użyciu SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="086a8-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="086a8-133">Dodaj odwołanie do System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="086a8-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="086a8-134">Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejącej instrukcji "Using".</span><span class="sxs-lookup"><span data-stu-id="086a8-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="086a8-135">Utwórz wystąpienie `WorkflowServiceHost` i Dodaj punkty końcowe dla usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="086a8-136">Konstruowanie obiektu `SqlWorkflowInstanceStoreBehavior` i Ustawianie właściwości obiektu Behavior.</span><span class="sxs-lookup"><span data-stu-id="086a8-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="086a8-137">Otwórz hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="086a8-138">Używanie właściwości DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="086a8-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="086a8-139">Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiony na obiekt `SqlWorkflowInstanceStore` utworzony przy użyciu wartości konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="086a8-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="086a8-140">Można to zrobić programowo, aby ustawić właściwość <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> `WorkflowServiceHost` bez używania klasy `SqlWorkflowInstanceStoreBehavior`, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="086a8-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="086a8-141">Włączanie trwałości dla hostowanych usług przepływu pracy, które używają obiektu WorkflowServiceHost przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="086a8-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="086a8-142">Możesz włączyć trwałość dla usługi przepływu pracy obsługiwanej przez samodzielny lub usługi aktywacji procesów systemu Windows (WAS) przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="086a8-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="086a8-143">Hostowana usługa przepływu pracy używa obiektu WorkflowServiceHost jako samoobsługowego usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="086a8-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="086a8-144">`SqlWorkflowInstanceStoreBehavior`, zachowanie usługi, które umożliwia wygodną zmianę właściwości [magazynu wystąpienia przepływu pracy SQL](sql-workflow-instance-store.md) za pomocą konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="086a8-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="086a8-145">W przypadku hostowanych usług przepływu pracy Użyj pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="086a8-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="086a8-146">Poniższy przykład konfiguracji pokazuje, jak skonfigurować magazyn wystąpień przepływu pracy SQL przy użyciu elementu zachowanie `sqlWorkflowInstanceStore` w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="086a8-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="086a8-147">Jeśli nie ustawisz wartości dla `connectionString` lub właściwości `connectionStringName`, magazyn wystąpień przepływu pracy SQL używa domyślnych nazwanych parametrów połączenia `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="086a8-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="086a8-148">Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiony na obiekt `SqlWorkflowInstanceStore` utworzony przy użyciu wartości konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="086a8-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="086a8-149">Można to zrobić programowo, aby użyć `SqlWorkflowInstanceStore` z `WorkflowServiceHost` bez użycia elementu zachowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="086a8-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="086a8-150">Zaleca się, aby nie przechowywać poufnych informacji, takich jak nazwy użytkowników i hasła w pliku Web. config.</span><span class="sxs-lookup"><span data-stu-id="086a8-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="086a8-151">Jeśli przechowujesz poufne informacje w pliku Web. config, należy zabezpieczyć dostęp do pliku Web. config za pomocą list Access Control systemu plików (ACL).</span><span class="sxs-lookup"><span data-stu-id="086a8-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="086a8-152">Ponadto można zabezpieczyć wartości konfiguracyjne w pliku konfiguracji, jak wspomniano w temacie [szyfrowanie informacji o konfiguracji za pomocą konfiguracji chronionej](https://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="086a8-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="086a8-153">Elementy Machine. config powiązane z funkcją magazynu wystąpień przepływu pracy SQL</span><span class="sxs-lookup"><span data-stu-id="086a8-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="086a8-154">Instalacja [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] dodaje następujące elementy związane z funkcją Magazyn wystąpień przepływu pracy SQL do pliku Machine. config:</span><span class="sxs-lookup"><span data-stu-id="086a8-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="086a8-155">Dodaje następujący element rozszerzenia zachowania do pliku Machine. config, tak aby można było użyć elementu \<obiekt SqlWorkflowInstanceStore >, w pliku konfiguracji, aby skonfigurować trwałość dla usług.</span><span class="sxs-lookup"><span data-stu-id="086a8-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
