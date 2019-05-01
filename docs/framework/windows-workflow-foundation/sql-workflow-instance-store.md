---
title: Magazyn wystąpień przepływu pracy SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 8314781f46d9cd4eddd06f6be95f8e952feef1b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004630"
---
# <a name="sql-workflow-instance-store"></a>Magazyn wystąpień przepływu pracy SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Jest dostarczany z programem SQL Store wystąpienia przepływu pracy, który umożliwia przepływy pracy, aby utrwalić informacje o stanie dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Ta funkcja jest zaimplementowany głównie w formie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> klasy, która jest pochodną abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> klasy framework trwałości. Funkcja Store wystąpienia przepływu pracy SQL stanowi dostawcy stanów trwałych programu SQL, który jest konkretną implementację trwałości interfejsu API, który korzysta z hosta do wysyłania poleceń trwałości do magazynu.  
  
 Store wystąpienia przepływu pracy SQL obsługuje zarówno własne przepływy pracy i usług przepływu pracy, które używają <xref:System.Activities.WorkflowApplication> lub <xref:System.ServiceModel.WorkflowServiceHost> oraz usług hostowanych w trybie <xref:System.ServiceModel.WorkflowServiceHost>. Funkcja Store wystąpienia przepływu pracy SQL samodzielnie hostowanej usługi można skonfigurować programowo przy użyciu modelu obiektu udostępnianych przez tę funkcję. Możesz skonfigurować tę funkcję dla usług hostowanych na <xref:System.ServiceModel.WorkflowServiceHost> programowo, za pomocą modelu obiektów, a także przy użyciu pliku konfiguracji XML.  
  
 Funkcja Store wystąpienia przepływu pracy SQL (**SqlWorkflowInstanceStore** klasy) nie implementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> i dlatego nie oferuje wsparcie trwałe usług WCF niezwiązanej z przepływem pracy. Ponadto nie implementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> i dlatego nie oferuje pomocy stanów trwałych dla przepływów pracy 3.x. Funkcja obsługuje przepływy pracy trwałości tylko WF 4.0 (i nowszych) i usług przepływu pracy. Tę funkcję również nie obsługuje żadnych baz danych innych niż SQL Server 2005 i SQL Server 2008.  
  
 Tematy w tej sekcji opisują właściwości i funkcji Store wystąpienia przepływu pracy SQL i udostępniać szczegółowe informacje na temat konfigurowania magazynu.  
  
 AppFabric w systemie Windows Server oferuje swój własny magazyn wystąpienia i narzędzi można uproszczenie konfiguracji i użytkowania magazyn wystąpienia. Aby uzyskać więcej informacji, zobacz [systemu Windows Server App Fabric wystąpienia Store](https://go.microsoft.com/fwlink/?LinkId=201201). Aby uzyskać więcej informacji o danych trwałości aplikacji Service Fabric programu SQL Server, zobacz [danych trwałości aplikacji Service Fabric programu SQL Server](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Właściwości magazynu wystąpień przepływu pracy SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Aktywacja wystąpienia](instance-activation.md)  
  
- [Obsługa zapytań](support-for-queries.md)  
  
- [Rozszerzalność magazynu](store-extensibility.md)  
  
- [Zabezpieczenia](security.md)  
  
- [Baza danych stanów trwałych programu SQL Server](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady trwałości](https://go.microsoft.com/fwlink/?LinkID=177735)
