---
title: Store wystąpienia przepływu pracy SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 680a233ca721cd8a0c620b797832419f460b13b6
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594288"
---
# <a name="sql-workflow-instance-store"></a>Store wystąpienia przepływu pracy SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Jest dostarczany z programem SQL Store wystąpienia przepływu pracy, który umożliwia przepływy pracy, aby utrwalić informacje o stanie dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Ta funkcja jest zaimplementowany głównie w formie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> klasy, która jest pochodną abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> klasy framework trwałości. Funkcja Store wystąpienia przepływu pracy SQL stanowi dostawcy stanów trwałych programu SQL, który jest konkretną implementację trwałości interfejsu API, który korzysta z hosta do wysyłania poleceń trwałości do magazynu.  
  
 Store wystąpienia przepływu pracy SQL obsługuje zarówno własne przepływy pracy i usług przepływu pracy, które używają <xref:System.Activities.WorkflowApplication> lub <xref:System.ServiceModel.WorkflowServiceHost> oraz usług hostowanych w trybie <xref:System.ServiceModel.WorkflowServiceHost>. Funkcja Store wystąpienia przepływu pracy SQL samodzielnie hostowanej usługi można skonfigurować programowo przy użyciu modelu obiektu udostępnianych przez tę funkcję. Możesz skonfigurować tę funkcję dla usług hostowanych na <xref:System.ServiceModel.WorkflowServiceHost> programowo, za pomocą modelu obiektów, a także przy użyciu pliku konfiguracji XML.  
  
 Funkcja Store wystąpienia przepływu pracy SQL (**SqlWorkflowInstanceStore** klasy) nie implementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> i dlatego nie oferuje wsparcie trwałe usług WCF niezwiązanej z przepływem pracy. Ponadto nie implementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> i dlatego nie oferuje pomocy stanów trwałych dla przepływów pracy 3.x. Funkcja obsługuje przepływy pracy trwałości tylko WF 4.0 (i nowszych) i usług przepływu pracy. Tę funkcję również nie obsługuje żadnych baz danych innych niż SQL Server 2005 i SQL Server 2008.  
  
 Tematy w tej sekcji opisują właściwości i funkcji Store wystąpienia przepływu pracy SQL i udostępniać szczegółowe informacje na temat konfigurowania magazynu.  
  
 AppFabric w systemie Windows Server oferuje swój własny magazyn wystąpienia i narzędzi można uproszczenie konfiguracji i użytkowania magazyn wystąpienia. Aby uzyskać więcej informacji, zobacz zobacz [systemu Windows Server App Fabric wystąpienia Store](https://go.microsoft.com/fwlink/?LinkId=201201). Aby uzyskać więcej informacji o danych trwałości aplikacji Service Fabric programu SQL Server, zobacz [danych trwałości aplikacji Service Fabric programu SQL Server](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Właściwości magazynu wystąpień przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Aktywacja wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Obsługa zapytań](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Rozszerzalność magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Zabezpieczenia](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [Baza danych stanów trwałych programu SQL Server](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości](https://go.microsoft.com/fwlink/?LinkID=177735)
