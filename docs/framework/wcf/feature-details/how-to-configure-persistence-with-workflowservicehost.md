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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Instrukcje: konfigurowanie trwałości za pomocą elementu WorkflowServiceHost
W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpień przepływu pracy SQL, <xref:System.ServiceModel.Activities.WorkflowServiceHost> aby włączyć trwałość przepływów pracy hostowanych przy użyciu pliku konfiguracyjnego. Przed użyciem funkcji magazynu wystąpień przepływu pracy SQL należy utworzyć bazę danych SQL, która jest używana do utrwalania wystąpień przepływu pracy. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Aby skonfigurować magazyn wystąpień przepływu pracy SQL w konfiguracji  
  
1. Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>zachowania usługi, które umożliwia zmianę ustawień za pomocą konfiguracji XML. W poniższym przykładzie konfiguracji pokazano, jak skonfigurować magazyn wystąpień `sqlWorkflowInstanceStore` przepływu pracy SQL przy użyciu <> elementu zachowania w pliku konfiguracji.  
  
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
  
     Aby uzyskać więcej informacji dotyczących konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji na temat `sqlWorkflowInstanceStore` poszczególnych ustawień elementu zachowania <>, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Sieci szkieletowej aplikacji systemu Windows Server udostępnia własny magazyn trwałości. Aby uzyskać więcej informacji, zobacz [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > W poprzednim przykładzie konfiguracji użyto uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Aby skonfigurować magazyn wystąpień przepływu pracy SQL w kodzie  
  
1. Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>zachowania usługi , która umożliwia zmianę ustawień za pomocą kodu. W poniższym przykładzie pokazano, jak skonfigurować magazyn <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> wystąpienia przepływu pracy SQL przy użyciu elementu zachowania w kodzie  
  
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
  
     Aby uzyskać więcej informacji dotyczących konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [Jak: Włączanie trwałości SQL dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji na <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> temat poszczególnych ustawień elementu zachowania, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Sieci szkieletowej aplikacji systemu Windows Server udostępnia własny magazyn trwałości. Aby uzyskać więcej informacji, zobacz [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > W poprzednim przykładzie konfiguracji użyto uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Na przykład sposób konfigurowania trwałości programowo zobacz [Jak: Włącz trwałość dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz też

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
