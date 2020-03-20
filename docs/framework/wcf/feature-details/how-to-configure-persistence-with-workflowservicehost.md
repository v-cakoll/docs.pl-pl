---
title: 'Instrukcje: konfigurowanie trwałości za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 2974b6bcbb94c5b54d91025aeabe7c2d2e94c7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185054"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="a1ba4-102">Instrukcje: konfigurowanie trwałości za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="a1ba4-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="a1ba4-103">W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpień przepływu pracy SQL, <xref:System.ServiceModel.Activities.WorkflowServiceHost> aby włączyć trwałość przepływów pracy hostowanych przy użyciu pliku konfiguracyjnego.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="a1ba4-104">Przed użyciem funkcji magazynu wystąpień przepływu pracy SQL należy utworzyć bazę danych SQL, która jest używana do utrwalania wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="a1ba4-105">Aby uzyskać więcej informacji, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="a1ba4-106">Aby skonfigurować magazyn wystąpień przepływu pracy SQL w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a1ba4-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="a1ba4-107">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>zachowania usługi, które umożliwia zmianę ustawień za pomocą konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="a1ba4-108">W poniższym przykładzie konfiguracji pokazano, jak skonfigurować magazyn wystąpień `sqlWorkflowInstanceStore` przepływu pracy SQL przy użyciu <> elementu zachowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="a1ba4-109">Aby uzyskać więcej informacji dotyczących konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="a1ba4-110">Aby uzyskać więcej informacji na temat `sqlWorkflowInstanceStore` poszczególnych ustawień elementu zachowania <>, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="a1ba4-111">Sieci szkieletowej aplikacji systemu Windows Server udostępnia własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="a1ba4-112">Aby uzyskać więcej informacji, zobacz [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1ba4-113">W poprzednim przykładzie konfiguracji użyto uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="a1ba4-114">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="a1ba4-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="a1ba4-115">Aby skonfigurować magazyn wystąpień przepływu pracy SQL w kodzie</span><span class="sxs-lookup"><span data-stu-id="a1ba4-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="a1ba4-116">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>zachowania usługi , która umożliwia zmianę ustawień za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="a1ba4-117">W poniższym przykładzie pokazano, jak skonfigurować magazyn <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> wystąpienia przepływu pracy SQL przy użyciu elementu zachowania w kodzie</span><span class="sxs-lookup"><span data-stu-id="a1ba4-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="a1ba4-118">Aby uzyskać więcej informacji dotyczących konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="a1ba4-119">Aby uzyskać więcej informacji na <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> temat poszczególnych ustawień elementu zachowania, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="a1ba4-120">Sieci szkieletowej aplikacji systemu Windows Server udostępnia własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="a1ba4-121">Aby uzyskać więcej informacji, zobacz [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1ba4-122">W poprzednim przykładzie konfiguracji użyto uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1ba4-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="a1ba4-123">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="a1ba4-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="a1ba4-124">Na przykład sposób konfigurowania trwałości programowo zobacz [Jak: Włącz trwałość dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1ba4-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ba4-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1ba4-125">See also</span></span>

- [<span data-ttu-id="a1ba4-126">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a1ba4-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="a1ba4-127">Trwałość przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a1ba4-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="a1ba4-128">[Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a1ba4-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
