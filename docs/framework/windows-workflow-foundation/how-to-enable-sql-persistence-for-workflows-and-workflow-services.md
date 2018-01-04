---
title: "Porady: Włącz trwałość SQL dla przepływów pracy i usług przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
caps.latest.revision: "36"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60fac3cba4da35b5146f777abd912ad15f0f29eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="bd268-102">Porady: Włącz trwałość SQL dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="bd268-102">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>
<span data-ttu-id="bd268-103">W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpienia przepływu pracy SQL do włączenia trwałości dla przepływów pracy i przepływ pracy usługi programowo i za pomocą pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>  
  
 <span data-ttu-id="bd268-104">Windows Server AppFabric upraszcza proces konfigurowania trwałości.</span><span class="sxs-lookup"><span data-stu-id="bd268-104">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="bd268-105">[Konfiguracji trwałości aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=201204)</span><span class="sxs-lookup"><span data-stu-id="bd268-105"> [App Fabric Persistence Configuration](http://go.microsoft.com/fwlink/?LinkId=201204)</span></span>  
  
 <span data-ttu-id="bd268-106">Przed użyciem funkcji magazynu wystąpienia przepływu pracy SQL, należy utworzyć bazę danych, która używa funkcji, aby utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-106">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="bd268-107">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Konfiguracji jest kopiowana skojarzony z funkcją magazynu wystąpienia przepływu pracy SQL do folderu %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN plików skryptów SQL.</span><span class="sxs-lookup"><span data-stu-id="bd268-107">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="bd268-108">Uruchom te pliki skryptów na bazie danych programu SQL Server 2005 lub SQL Server 2008, które mają w magazynie wystąpień przepływu pracy SQL do użycia, aby utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-108">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="bd268-109">Uruchom plik SqlWorkflowInstanceStoreSchema.sql najpierw, a następnie uruchom plik SqlWorkflowInstanceStoreLogic.sql.</span><span class="sxs-lookup"><span data-stu-id="bd268-109">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd268-110">Aby wyczyścić trwałości bazy danych ma nową bazą danych, należy uruchomić skrypty w %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN w następującej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bd268-110">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>  
>   
>  1.  <span data-ttu-id="bd268-111">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="bd268-111">SqlWorkflowInstanceStoreSchema.sql</span></span>  
> 2.  <span data-ttu-id="bd268-112">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="bd268-112">SqlWorkflowInstanceStoreLogic.sql</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd268-113">Jeśli nie utworzysz bazę danych trwałości, funkcję Magazyn wystąpienia przepływu pracy SQL zgłasza wyjątek podobny do następującego hosta próba utrwalić przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-113">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>  
>   
>  <span data-ttu-id="bd268-114">System.Data.SqlClient.SqlException: Nie można odnaleźć procedury składowanej "System.Activities.DurableInstancing.CreateLockOwner"</span><span class="sxs-lookup"><span data-stu-id="bd268-114">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>  
  
 <span data-ttu-id="bd268-115">W poniższych sekcjach opisano sposób włączania trwałości dla przepływów pracy i usług przepływu pracy przy użyciu magazynu wystąpienia przepływu pracy SQL.</span><span class="sxs-lookup"><span data-stu-id="bd268-115">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="bd268-116">właściwości magazynu wystąpienia przepływu pracy SQL, zobacz [właściwości z przepływu pracy wystąpienia magazynu SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="bd268-116"> properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md).</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="bd268-117">Włączenie trwałości dla przepływów pracy Self-Hosted, używanego przez obiekt WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="bd268-117">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>  
 <span data-ttu-id="bd268-118">Można włączyć trwałości dla siebie przepływy pracy używające <xref:System.Activities.WorkflowApplication> programowo przy użyciu <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="bd268-118">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="bd268-119">Poniższa procedura zawiera kroki, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="bd268-119">The following procedure contains steps to do this.</span></span>  
  
#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="bd268-120">Aby włączyć trwałości dla siebie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="bd268-120">To enable persistence for self-hosted workflows</span></span>  
  
1.  <span data-ttu-id="bd268-121">Dodaj odwołanie do System.Activites.DurableInstancing.dll.</span><span class="sxs-lookup"><span data-stu-id="bd268-121">Add a reference to System.Activites.DurableInstancing.dll.</span></span>  
  
2.  <span data-ttu-id="bd268-122">Dodaj następującą instrukcję na początku pliku źródłowego po istniejących instrukcji "using".</span><span class="sxs-lookup"><span data-stu-id="bd268-122">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.Activities.DurableInstancing;  
    ```  
  
3.  <span data-ttu-id="bd268-123">Utworzyć <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> i przypisz go do <xref:System.Activities.WorkflowApplication.InstanceStore%2A> z <xref:System.Activities.WorkflowApplication> jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="bd268-123">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStore store =   
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");  
  
    WorkflowApplication wfApp =  
        new WorkflowApplication(new Workflow1());  
  
    wfApp.InstanceStore = store;  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="bd268-124">W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być różne.</span><span class="sxs-lookup"><span data-stu-id="bd268-124">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
4.  <span data-ttu-id="bd268-125">Wywołanie <xref:System.Activities.WorkflowApplication.Persist%2A> metoda <xref:System.Activities.WorkflowApplication> obiekt, aby utrwalić przepływu pracy, lub <xref:System.Activities.WorkflowApplication.Unload%2A> metodę, aby utrwalić i zwolnić przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-125">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="bd268-126">Można również obsługiwać <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> zdarzenie zgłaszane przez <xref:System.Activities.WorkflowApplication> obiektu i zwraca odpowiednie (<xref:System.Activities.PersistableIdleAction.Persist> lub <xref:System.Activities.PersistableIdleAction.Unload>) członek <xref:System.Activities.PersistableIdleAction>.</span><span class="sxs-lookup"><span data-stu-id="bd268-126">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>  
  
    ```csharp  
    wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)  
    {  
        return PersistableIdleAction.Persist;  
    };  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="bd268-127">Zobacz [utrwalanie aplikacji przepływu pracy](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) na przykład [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) przykład włączenie trwałości dla przepływów pracy za pomocą <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>i [porady: tworzenie i uruchamianie długi Uruchamiania przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) kroku [Wprowadzenie — samouczek](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) instrukcje krok po kroku.</span><span class="sxs-lookup"><span data-stu-id="bd268-127">See the [Persisting a Workflow Application](../../../docs/framework/windows-workflow-foundation/samples/persisting-a-workflow-application.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflows using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, and the [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) for step by step instructions.</span></span>  
  
## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="bd268-128">Włączenie trwałości dla usługi przepływu pracy Self-Hosted używanego WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="bd268-128">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>  
 <span data-ttu-id="bd268-129">Można włączyć trwałości dla usług hostowania samoobsługowego przepływu pracy, które używają <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy lub <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> klasy.</span><span class="sxs-lookup"><span data-stu-id="bd268-129">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>  
  
### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="bd268-130">Za pomocą klasy SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="bd268-130">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>  
 <span data-ttu-id="bd268-131">Poniższa procedura zawiera kroki, aby użyć <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> klasy w celu włączenia trwałości dla usługi hostowanej własnym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-131">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>  
  
##### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="bd268-132">Aby umożliwić utrwalenie za pomocą SqlWorkflowInstanceStoreBehavior</span><span class="sxs-lookup"><span data-stu-id="bd268-132">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>  
  
1.  <span data-ttu-id="bd268-133">Dodaj odwołanie do System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="bd268-133">Add a reference to the System.ServiceModel.dll.</span></span>  
  
2.  <span data-ttu-id="bd268-134">Dodaj następującą instrukcję na początku pliku źródłowego po istniejących instrukcji "using".</span><span class="sxs-lookup"><span data-stu-id="bd268-134">Add the following statement at the top of the source file after the existing "using" statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Activities.Description;  
    ```  
  
3.  <span data-ttu-id="bd268-135">Utwórz wystąpienie `WorkflowServiceHost` i dodać punkty końcowe usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-135">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>  
  
    ```  
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));  
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");  
    ```  
  
4.  <span data-ttu-id="bd268-136">Utworzyć `SqlWorkflowInstanceStoreBehavior` obiektu i można ustawić właściwości obiektu zachowanie.</span><span class="sxs-lookup"><span data-stu-id="bd268-136">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>  
  
    ```csharp  
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);  
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);  
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;  
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;  
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");  
    host.Description.Behaviors.Add(instanceStoreBehavior);  
    ```  
  
5.  <span data-ttu-id="bd268-137">Otworzyć hosta usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-137">Open the workflow service host.</span></span>  
  
    ```vb  
    host.Open();  
    ```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd268-138">Zobacz [wbudowanych konfiguracji](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) na przykład [trwałości](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) przykład włączenie trwałości dla usługi przepływu pracy przy użyciu `SqlWorkflowInstanceStoreBehavior` klasy.</span><span class="sxs-lookup"><span data-stu-id="bd268-138">See the [Built-in Configuration](../../../docs/framework/windows-workflow-foundation/samples/built-in-configuration.md) sample at [Persistence](../../../docs/framework/windows-workflow-foundation/samples/persistence.md) for an example of enabling persistence for workflow services using the `SqlWorkflowInstanceStoreBehavior` class.</span></span>  
  
### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="bd268-139">Za pomocą właściwości DurableInstancingOptions</span><span class="sxs-lookup"><span data-stu-id="bd268-139">Using the DurableInstancingOptions Property</span></span>  
 <span data-ttu-id="bd268-140">Gdy `SqlWorkflowInstanceStoreBehavior` zostanie zastosowana, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` ma ustawioną wartość `SqlWorkflowInstanceStore` obiektów utworzonych przy użyciu wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="bd268-141">Należy je programowo, aby ustawić <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> właściwość `WorkflowServiceHost` bez użycia `SqlWorkflowInstanceStoreBehavior` klasy, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="bd268-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="bd268-142">Włączenie trwałości dla usługi przepływu pracy WAS-Hosted używanego WorkflowServiceHost przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bd268-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>  
 <span data-ttu-id="bd268-143">W przypadku włączenia trwałości dla usług hostowania samoobsługowego lub hostowana usługa aktywacji procesów systemu Windows WAS przepływu pracy, przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="bd268-144">Usługa hostowana usługa WAS przepływ pracy używa WorkflowServiceHost jak usług hostowania samoobsługowego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="bd268-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>  
  
 <span data-ttu-id="bd268-145">`SqlWorkflowInstanceStoreBehavior`, Zachowanie usługi, która pozwala łatwo zmienić [magazyn wystąpienia przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) właściwości za pośrednictwem pliku XML konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="bd268-146">Dla usługi hostowanej WAS przepływu pracy Użyj pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="bd268-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="bd268-147">W poniższym przykładzie konfiguracji pokazano, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu `sqlWorkflowInstanceStore` zachowanie elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="bd268-148">Jeśli nie należy ustawiać wartości `connectionString` lub `connectionStringName` właściwość, w magazynie wystąpień przepływu pracy SQL używa domyślnie nazwane parametry połączenia `DefaultSqlWorkflowInstanceStoreConnectionString`.</span><span class="sxs-lookup"><span data-stu-id="bd268-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>  
  
 <span data-ttu-id="bd268-149">Gdy `SqlWorkflowInstanceStoreBehavior` zostanie zastosowana, `DurableInstancingOptions.InstanceStore` na `WorkflowServiceHost` ma ustawioną wartość `SqlWorkflowInstanceStore` obiektów utworzonych przy użyciu wartości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="bd268-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="bd268-150">Należy je programowo, aby użyć `SqlWorkflowInstanceStore` z `WorkflowServiceHost` bez za pomocą elementu zachowania usługi.</span><span class="sxs-lookup"><span data-stu-id="bd268-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>  
  
```  
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="bd268-151">Zaleca się, że poufne informacje, takie jak nazwy użytkowników i hasła nie są przechowywane w pliku Web.config.</span><span class="sxs-lookup"><span data-stu-id="bd268-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="bd268-152">Jeśli w pliku Web.config są przechowywane poufne informacje, należy zabezpieczyć dostęp do pliku Web.config przy użyciu list kontroli dostępu (ACL) w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="bd268-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="bd268-153">Ponadto można także zabezpieczyć wartości konfiguracji w pliku konfiguracji jak wspomniano w [szyfrowania informacji przy użyciu chronione Konfiguracja](http://go.microsoft.com/fwlink/?LinkId=178419).</span><span class="sxs-lookup"><span data-stu-id="bd268-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](http://go.microsoft.com/fwlink/?LinkId=178419).</span></span>  
  
### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="bd268-154">Elementy Machine.config powiązanych z tą funkcją magazynu wystąpienia przepływu pracy SQL</span><span class="sxs-lookup"><span data-stu-id="bd268-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>  
 <span data-ttu-id="bd268-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Instalacji doda następujące elementy związane z funkcji magazynu wystąpienia przepływu pracy SQL w pliku Machine.config:</span><span class="sxs-lookup"><span data-stu-id="bd268-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>  
  
-   <span data-ttu-id="bd268-156">Dodaje następujący element rozszerzenia zachowania do pliku Machine.config, dzięki czemu można używać <`sqlWorkflowInstanceStore`> Usługa zachowanie elementu w pliku konfiguracyjnym Konfigurowanie trwałości dla usługi.</span><span class="sxs-lookup"><span data-stu-id="bd268-156">Adds the following behavior extension element to the Machine.config file so that you can use the <`sqlWorkflowInstanceStore`> service behavior element in the configuration file to configure persistence for your services.</span></span>  
  
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
