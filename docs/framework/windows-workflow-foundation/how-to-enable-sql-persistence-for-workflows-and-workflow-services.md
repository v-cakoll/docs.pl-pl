---
title: 'Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 84a9220e39c0d79dc53bee576735d1062c1c037c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779213"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="c13f1-102">Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c13f1-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="c13f1-103">W tym temacie opisano sposób konfigurowania funkcji Store wystąpienia przepływu pracy SQL Włączanie stanów trwałych dla przepływów pracy i usługi przepływu pracy, zarówno programowo i za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13f1-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="c13f1-104">Windows Server AppFabric upraszcza proces konfigurowania trwałości.</span><span class="sxs-lookup"><span data-stu-id="c13f1-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="c13f1-105">Aby uzyskać więcej informacji, zobacz [konfiguracji trwałości sieci szkieletowej aplikacji](https://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="c13f1-105">For more information, see [App Fabric Persistence Configuration](https://go.microsoft.com/fwlink/?LinkId=201204)</span></span>

<span data-ttu-id="c13f1-106">Przed użyciem funkcji Store wystąpienia przepływu pracy SQL, należy utworzyć bazy danych, która korzysta z tej funkcji można utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="c13f1-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Konfiguracji jest kopiowana skojarzonego z funkcją Store wystąpienia przepływu pracy SQL do folderu %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN pliki skryptu SQL.</span><span class="sxs-lookup"><span data-stu-id="c13f1-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="c13f1-108">Uruchom te pliki skryptów względem bazy danych programu SQL Server 2005 lub SQL Server 2008 mają Store wystąpienia przepływu pracy SQL, można użyć, aby utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="c13f1-109">Uruchom plik SqlWorkflowInstanceStoreSchema.sql najpierw, a następnie uruchom plik SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="c13f1-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="c13f1-110">Aby wyczyścić trwałości bazy danych do nowej bazy danych, uruchom skrypty w %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN w następującej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c13f1-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="c13f1-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="c13f1-111">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="c13f1-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="c13f1-112">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c13f1-113">Jeśli nie utworzysz bazę danych trwałości, funkcja Store wystąpienia przepływu pracy SQL zgłasza wyjątek podobny do następującego, gdy host próbuje zachować przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="c13f1-114">System.Data.SqlClient.SqlException: Nie można odnaleźć procedury składowanej "System.Activities.DurableInstancing.CreateLockOwner"</span><span class="sxs-lookup"><span data-stu-id="c13f1-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="c13f1-115">Poniżej opisano sposób włączania stanów trwałych dla przepływów pracy i usług przepływu pracy przy użyciu Store wystąpienia przepływu pracy SQL.</span><span class="sxs-lookup"><span data-stu-id="c13f1-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="c13f1-116">Aby uzyskać więcej informacji na temat właściwości Store wystąpienia przepływu pracy SQL, zobacz [właściwości programu SQL przepływu pracy wystąpienie Store](properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="c13f1-116">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="c13f1-117">Włączanie stanów trwałych dla przepływów pracy z produktem, używanego przez WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="c13f1-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="c13f1-118">Możesz włączyć trwałość Self-Hosted przepływach pracy korzystających <xref:System.Activities.WorkflowApplication> programowo przy użyciu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="c13f1-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="c13f1-119">Poniższa procedura zawiera kroki, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c13f1-119">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="c13f1-120">Aby włączyć opcję trwałości Self-Hosted przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="c13f1-120">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="c13f1-121">Dodaj odwołanie do System.Activities.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="c13f1-121">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="c13f1-122">Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejących instrukcjach "za pomocą".</span><span class="sxs-lookup"><span data-stu-id="c13f1-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="c13f1-123">Konstruowania <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> i przypisz ją do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c13f1-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="c13f1-124">W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być inny.</span><span class="sxs-lookup"><span data-stu-id="c13f1-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="c13f1-125">Wywoływanie <xref:System.Activities.WorkflowApplication.Persist%2A> metody <xref:System.Activities.WorkflowApplication> obiektu, aby utrwalić przepływu pracy, lub <xref:System.Activities.WorkflowApplication.Unload%2A> metodę, aby utrwalić i zwalnianie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="c13f1-126">Może również obsługiwać <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzenia wygenerowane przez <xref:System.Activities.WorkflowApplication> obiektu i zwraca odpowiednią (<xref:System.Activities.PersistableIdleAction.Persist> lub <xref:System.Activities.PersistableIdleAction.Unload>) członkiem <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="c13f1-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="c13f1-127">Zobacz [jak: Tworzenie i uruchamianie długiego uruchamiania przepływu pracy](how-to-create-and-run-a-long-running-workflow.md) kroku [Samouczek wprowadzający](getting-started-tutorial.md) instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="c13f1-127">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="c13f1-128">Włączanie stanów trwałych dla produktu usług przepływu pracy, które korzystają WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="c13f1-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="c13f1-129">Możesz włączyć trwałość dla usługi samodzielnie hostowanej przepływu pracy, które korzystają z <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy lub <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> klasy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="c13f1-130">Używanie klasy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="c13f1-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="c13f1-131">Poniższa procedura zawiera kroki, aby użyć <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy, aby włączyć opcję trwałości dla usługi samodzielnie hostowanej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="c13f1-132">Aby włączyć opcję trwałości za pomocą SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="c13f1-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="c13f1-133">Dodaj odwołanie do System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="c13f1-133">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="c13f1-134">Dodaj następującą instrukcję w górnej części pliku źródłowego po istniejących instrukcjach "za pomocą".</span><span class="sxs-lookup"><span data-stu-id="c13f1-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="c13f1-135">Utwórz wystąpienie obiektu `WorkflowServiceHost` i dodać punkty końcowe usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="c13f1-136">Konstruowania `SqlWorkflowInstanceStoreBehavior` obiektu i ustawienie właściwości obiektu zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c13f1-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="c13f1-137">Otwórz hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-137">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="c13f1-138">Przy użyciu właściwości DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="c13f1-138">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="c13f1-139">Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiona na `SqlWorkflowInstanceStore` obiekt utworzony przy użyciu wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13f1-139">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="c13f1-140">Dzieje się tak samo, programowo, aby ustawić <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> właściwość `WorkflowServiceHost` bez użycia `SqlWorkflowInstanceStoreBehavior` klasy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="c13f1-140">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="c13f1-141">Włączanie stanów trwałych dla WAS-Hosted usług przepływu pracy, które korzystają WorkflowServiceHost przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="c13f1-141">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="c13f1-142">Możesz włączyć trwałość usługi samodzielnie hostowanej lub hostowany Windows Process Activation Service WAS przepływu pracy przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13f1-142">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="c13f1-143">Usługa hostowana WAS przepływ pracy używa WorkflowServiceHost w usługach samodzielnie hostowanej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c13f1-143">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="c13f1-144">`SqlWorkflowInstanceStoreBehavior`, Zachowanie usługi, które umożliwia zmianę wygodnie [Store wystąpienia przepływu pracy SQL](sql-workflow-instance-store.md) właściwości za pomocą konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="c13f1-144">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="c13f1-145">Hostowana WAS usług przepływu pracy można użyć w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="c13f1-145">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="c13f1-146">W poniższym przykładzie konfiguracji przedstawia sposób konfigurowania Store wystąpienia przepływu pracy SQL przy użyciu `sqlWorkflowInstanceStore` zachowania elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13f1-146">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

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

<span data-ttu-id="c13f1-147">Jeśli nie ustawisz wartości `connectionString` lub `connectionStringName` właściwości Store wystąpienia przepływu pracy SQL korzysta z domyślnego o nazwie parametry połączenia `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="c13f1-147">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="c13f1-148">Gdy `SqlWorkflowInstanceStoreBehavior` jest stosowany `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` jest ustawiona na `SqlWorkflowInstanceStore` obiekt utworzony przy użyciu wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c13f1-148">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="c13f1-149">Dzieje się tak samo, programowo, aby użyć `SqlWorkflowInstanceStore` z `WorkflowServiceHost` bez użycia elementu zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="c13f1-149">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="c13f1-150">Zaleca się, że poufne informacje, takie jak nazwy użytkowników i hasła nie są przechowywane w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="c13f1-150">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="c13f1-151">Jeśli w pliku Web.config są przechowywane poufne informacje, należy zabezpieczyć dostęp do pliku Web.config przy użyciu systemu plików list kontroli dostępu (ACL).</span><span class="sxs-lookup"><span data-stu-id="c13f1-151">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="c13f1-152">Ponadto można także zabezpieczyć wartości konfiguracji w pliku konfiguracji zgodnie z opisem w [szyfrowania informacji przy użyciu chronione Konfiguracja](https://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="c13f1-152">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](https://go.microsoft.com/fwlink/?LinkId=178419).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="c13f1-153">Machine.config elementów powiązanych z tą funkcją Store wystąpienia przepływu pracy SQL</span><span class="sxs-lookup"><span data-stu-id="c13f1-153">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="c13f1-154">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalacja dodaje następujące elementy związane z funkcją Store wystąpienia przepływu pracy SQL do pliku Machine.config:</span><span class="sxs-lookup"><span data-stu-id="c13f1-154">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="c13f1-155">Dodaje do pliku Machine.config następujący element rozszerzenia zachowania, tak, aby można było używać \<sqlWorkflowInstanceStore > element zachowanie usługi, w pliku konfiguracyjnym Konfigurowanie trwałości dla usługi.</span><span class="sxs-lookup"><span data-stu-id="c13f1-155">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

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
