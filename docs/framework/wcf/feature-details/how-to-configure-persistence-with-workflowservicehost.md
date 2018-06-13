---
title: 'Porady: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 9035ded1ca533d9b2107d90f605e15c9ce915965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493206"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="e867c-102">Porady: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="e867c-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="e867c-103">W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpienia przepływu pracy SQL do włączenia trwałości dla przepływów pracy obsługiwanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost> przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e867c-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="e867c-104">Przed użyciem funkcji magazynu wystąpienia przepływu pracy SQL należy utworzyć bazę danych SQL używanego w taki sposób, aby utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e867c-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="e867c-105">Aby uzyskać więcej informacji, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="e867c-106">Aby skonfigurować Magazyn wystąpienia przepływu pracy SQL w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e867c-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1.  <span data-ttu-id="e867c-107">Właściwości magazynu wystąpienia przepływu pracy SQL można skonfigurować za pośrednictwem <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, która umożliwia zmianę ustawień za pomocą pliku XML konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e867c-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="e867c-108">W poniższym przykładzie konfiguracji pokazano, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu <`sqlWorkflowInstanceStore`> Zachowanie elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e867c-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="e867c-109">Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpienia przepływu pracy SQL, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="e867c-110">Aby uzyskać więcej informacji o poszczególnych ustawieniach dla <`sqlWorkflowInstanceStore`> element zachowania, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e867c-111">Windows Server AppFabric zapewnia magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="e867c-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="e867c-112">Aby uzyskać więcej informacji, zobacz [systemu Windows Server aplikacji sieci szkieletowej trwałości](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="e867c-112">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e867c-113">W poprzednim przykładzie konfiguracji używa uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="e867c-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="e867c-114">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e867c-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="e867c-115">Aby skonfigurować Magazyn wystąpienia przepływu pracy SQL w kodzie</span><span class="sxs-lookup"><span data-stu-id="e867c-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1.  <span data-ttu-id="e867c-116">Właściwości magazynu wystąpienia przepływu pracy SQL można skonfigurować za pośrednictwem <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, która umożliwia zmianę ustawień za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="e867c-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="e867c-117">Poniższy przykład pokazuje, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> element zachowania w kodzie</span><span class="sxs-lookup"><span data-stu-id="e867c-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     <span data-ttu-id="e867c-118">Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpienia przepływu pracy SQL, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="e867c-119">Aby uzyskać więcej informacji o poszczególnych ustawieniach dla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> element zachowania, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="e867c-120">Windows Server AppFabric zapewnia magazynie trwałości.</span><span class="sxs-lookup"><span data-stu-id="e867c-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="e867c-121">Aby uzyskać więcej informacji, zobacz [systemu Windows Server aplikacji sieci szkieletowej trwałości](http://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="e867c-121">For more information, see [Windows Server App Fabric Persistence](http://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e867c-122">W poprzednim przykładzie konfiguracji używa uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="e867c-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="e867c-123">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="e867c-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="e867c-124">Przykład sposobu konfigurowania trwałości programowo w temacie [porady: Włącz trwałość dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="e867c-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e867c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e867c-125">See Also</span></span>  
 [<span data-ttu-id="e867c-126">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e867c-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="e867c-127">Trwałość przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e867c-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [<span data-ttu-id="e867c-128">Windows Server AppFabric trwałości</span><span class="sxs-lookup"><span data-stu-id="e867c-128">Windows Server App Fabric Persistence</span></span>](http://go.microsoft.com/fwlink/?LinkId=193121)
