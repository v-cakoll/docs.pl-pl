---
title: 'Instrukcje: konfigurowanie trwałości za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: b8839f42a9b8b5f4da0a1a8364c7eac5a4c06d4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699776"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="298e0-102">Instrukcje: konfigurowanie trwałości za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="298e0-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="298e0-103">W tym temacie opisano sposób konfigurowania funkcji Store wystąpienia przepływu pracy SQL, aby włączyć opcję trwałości dla przepływów pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost> przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="298e0-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="298e0-104">Przed użyciem funkcji Store wystąpienia przepływu pracy SQL należy utworzyć bazę danych SQL jest używany, aby utrwalić wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="298e0-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="298e0-105">Aby uzyskać więcej informacji, zobacz [jak: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="298e0-106">Aby skonfigurować Store wystąpienia przepływu pracy SQL w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="298e0-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="298e0-107">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, które umożliwia zmianę ustawień konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="298e0-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="298e0-108">W poniższym przykładzie konfiguracji pokazuje, jak skonfigurować Magazyn wystąpień przepływu pracy SQL za pomocą <`sqlWorkflowInstanceStore`> zachowania elementu w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="298e0-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="298e0-109">Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [jak: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="298e0-110">Aby uzyskać więcej informacji na temat poszczególnych ustawień dla <`sqlWorkflowInstanceStore`> element zachowania, zobacz [Store wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="298e0-111">AppFabric w systemie Windows Server udostępnia własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="298e0-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="298e0-112">Aby uzyskać więcej informacji, zobacz [systemu Windows Server App Fabric trwałości](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="298e0-112">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="298e0-113">W poprzednim przykładzie konfiguracja użyto uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="298e0-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="298e0-114">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="298e0-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="298e0-115">Aby skonfigurować Store wystąpienia przepływu pracy SQL w kodzie</span><span class="sxs-lookup"><span data-stu-id="298e0-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="298e0-116">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, które umożliwia zmianę ustawień za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="298e0-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="298e0-117">Poniższy przykład pokazuje, jak skonfigurować Magazyn wystąpień przepływu pracy SQL przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> zachowania elementu w kodzie</span><span class="sxs-lookup"><span data-stu-id="298e0-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="298e0-118">Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [jak: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="298e0-119">Aby uzyskać więcej informacji na temat poszczególnych ustawień <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> zachowanie elementu, zobacz [Store wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="298e0-120">AppFabric w systemie Windows Server udostępnia własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="298e0-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="298e0-121">Aby uzyskać więcej informacji, zobacz [systemu Windows Server App Fabric trwałości](https://go.microsoft.com/fwlink/?LinkId=193121).</span><span class="sxs-lookup"><span data-stu-id="298e0-121">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="298e0-122">W poprzednim przykładzie konfiguracja użyto uproszczona konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="298e0-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="298e0-123">Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="298e0-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="298e0-124">Przykład sposobu konfigurowania trwałości programowo zobacz [jak: Włączanie stanów trwałych dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="298e0-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298e0-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="298e0-125">See also</span></span>

- [<span data-ttu-id="298e0-126">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="298e0-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="298e0-127">Trwałość przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="298e0-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [<span data-ttu-id="298e0-128">Windows Server AppFabric trwałości</span><span class="sxs-lookup"><span data-stu-id="298e0-128">Windows Server App Fabric Persistence</span></span>](https://go.microsoft.com/fwlink/?LinkId=193121)
