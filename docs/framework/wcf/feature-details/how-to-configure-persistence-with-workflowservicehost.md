---
title: 'Instrukcje: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 7b65b89db674a624f7dfbf8ca816e0f0c2d2ff80
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963478"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="b04e2-102">Instrukcje: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="b04e2-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="b04e2-103">W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpień przepływu pracy SQL w celu włączenia trwałości dla przepływów pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost> przy użyciu pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b04e2-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="b04e2-104">Przed użyciem funkcji magazynu wystąpień przepływu pracy SQL należy utworzyć bazę danych SQL, która jest używana do utrwalania wystąpień przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b04e2-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="b04e2-105">Aby uzyskać więcej informacji, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="b04e2-106">Aby skonfigurować magazyn wystąpień przepływu pracy SQL w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b04e2-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="b04e2-107">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowania usługi, które pozwala na zmianę ustawień za pomocą konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="b04e2-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="b04e2-108">Poniższy przykład konfiguracji przedstawia sposób konfigurowania magazynu wystąpień przepływu pracy SQL przy użyciu <`sqlWorkflowInstanceStore`> elementu zachowanie w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="b04e2-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
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
  
     <span data-ttu-id="b04e2-109">Aby uzyskać więcej informacji o sposobie konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="b04e2-110">Aby uzyskać więcej informacji na temat poszczególnych ustawień dla elementu <`sqlWorkflowInstanceStore`> Behavior, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="b04e2-111">Sieć szkieletowa aplikacji systemu Windows Server udostępnia swój własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="b04e2-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="b04e2-112">Aby uzyskać więcej informacji, zobacz [trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="b04e2-112">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b04e2-113">Poprzedni przykład konfiguracji używa uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b04e2-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="b04e2-114">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b04e2-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="b04e2-115">Aby skonfigurować magazyn wystąpień przepływu pracy SQL w kodzie</span><span class="sxs-lookup"><span data-stu-id="b04e2-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="b04e2-116">Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowania usługi, które pozwala na zmianę ustawień za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="b04e2-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="b04e2-117">Poniższy przykład pokazuje, jak skonfigurować magazyn wystąpień przepływu pracy SQL przy użyciu elementu zachowanie <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> w kodzie</span><span class="sxs-lookup"><span data-stu-id="b04e2-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
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
  
     <span data-ttu-id="b04e2-118">Aby uzyskać więcej informacji o sposobie konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="b04e2-119">Aby uzyskać więcej informacji na temat poszczególnych ustawień dla elementu zachowanie <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zobacz [Magazyn wystąpień usługi SQL Workflow](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="b04e2-120">Sieć szkieletowa aplikacji systemu Windows Server udostępnia swój własny magazyn trwałości.</span><span class="sxs-lookup"><span data-stu-id="b04e2-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="b04e2-121">Aby uzyskać więcej informacji, zobacz [trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span><span class="sxs-lookup"><span data-stu-id="b04e2-121">For more information, see [Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b04e2-122">Poprzedni przykład konfiguracji używa uproszczonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b04e2-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="b04e2-123">Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b04e2-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="b04e2-124">Przykład sposobu konfiguracji usługi trwałości można znaleźć w temacie [jak: włączyć trwałość dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="b04e2-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04e2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b04e2-125">See also</span></span>

- [<span data-ttu-id="b04e2-126">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b04e2-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="b04e2-127">Trwałość przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b04e2-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- <span data-ttu-id="b04e2-128">[Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b04e2-128">[Windows Server App Fabric Persistence](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))</span></span>
