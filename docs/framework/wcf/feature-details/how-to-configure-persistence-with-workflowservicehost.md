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
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Instrukcje: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost
W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpień przepływu pracy SQL w celu włączenia trwałości dla przepływów pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost> przy użyciu pliku konfiguracji. Przed użyciem funkcji magazynu wystąpień przepływu pracy SQL należy utworzyć bazę danych SQL, która jest używana do utrwalania wystąpień przepływu pracy. Aby uzyskać więcej informacji, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Aby skonfigurować magazyn wystąpień przepływu pracy SQL w konfiguracji  
  
1. Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowania usługi, które pozwala na zmianę ustawień za pomocą konfiguracji XML. Poniższy przykład konfiguracji przedstawia sposób konfigurowania magazynu wystąpień przepływu pracy SQL przy użyciu <`sqlWorkflowInstanceStore`> elementu zachowanie w pliku konfiguracyjnym.  
  
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
  
     Aby uzyskać więcej informacji o sposobie konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji na temat poszczególnych ustawień dla elementu <`sqlWorkflowInstanceStore`> Behavior, zobacz [Magazyn wystąpień przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Sieć szkieletowa aplikacji systemu Windows Server udostępnia swój własny magazyn trwałości. Aby uzyskać więcej informacji, zobacz [trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Aby skonfigurować magazyn wystąpień przepływu pracy SQL w kodzie  
  
1. Właściwości magazynu wystąpień przepływu pracy SQL można skonfigurować za pomocą <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowania usługi, które pozwala na zmianę ustawień za pomocą kodu. Poniższy przykład pokazuje, jak skonfigurować magazyn wystąpień przepływu pracy SQL przy użyciu elementu zachowanie <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> w kodzie  
  
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
  
     Aby uzyskać więcej informacji o sposobie konfigurowania magazynu wystąpień przepływu pracy SQL, zobacz [How to: Enable SQL trwałości dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji na temat poszczególnych ustawień dla elementu zachowanie <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zobacz [Magazyn wystąpień usługi SQL Workflow](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Sieć szkieletowa aplikacji systemu Windows Server udostępnia swój własny magazyn trwałości. Aby uzyskać więcej informacji, zobacz [trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)).  
  
    > [!NOTE]
    > Poprzedni przykład konfiguracji używa uproszczonej konfiguracji. Aby uzyskać więcej informacji, zobacz [Uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Przykład sposobu konfiguracji usługi trwałości można znaleźć w temacie [jak: włączyć trwałość dla przepływów pracy i usług przepływu pracy](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [Trwałość sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10))
