---
title: Magazyn wystąpienia przepływu pracy SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60eaef2bbbb2ff7653aeac832163276c32bc696b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="sql-workflow-instance-store"></a>Magazyn wystąpienia przepływu pracy SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Jest dostarczany z SQL magazyn wystąpienia przepływu pracy, dzięki czemu przepływy pracy, aby zachować informacje o stanie dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008. Ta funkcja jest głównie zaimplementowana w formie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> klasy, która pochodzi z klasy abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> klasy framework trwałości. Funkcja magazynu wystąpienia przepływu pracy SQL stanowi SQL dostawcy trwałości, który jest konkretną implementację trwałości interfejsu API używany przez hosta do wysyłania polecenia trwałości w magazynie.  
  
 W magazynie wystąpień przepływu pracy SQL obsługuje zarówno siebie przepływy pracy lub usług przepływu pracy, które używają <xref:System.Activities.WorkflowApplication> lub <xref:System.ServiceModel.WorkflowServiceHost> oraz usług hostowanych w trybie <xref:System.ServiceModel.WorkflowServiceHost>. Funkcja magazynu wystąpienia przepływu pracy SQL dla usług hostowania samoobsługowego można skonfigurować programowo przy użyciu model obiektowy udostępniany przez funkcję. Można skonfigurować tej funkcji dla usług hostowanych na <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu modelu obiektu, a także za pomocą pliku konfiguracji XML.  
  
 Funkcja magazynu wystąpienia przepływu pracy SQL (**SqlWorkflowInstanceStore** klasy) nie implementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> i dlatego nie oferuje obsługę trwałości trwałe usługi WCF bez przepływu pracy. Również nie implementuje on <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> i dlatego nie oferuje pomocy trwałości dla przepływów pracy 3.x. Gdy funkcja obsługuje przepływy pracy trwałości tylko WF 4.0 (i nowszych) i usług przepływu pracy. Funkcja nie obsługuje również żadnych baz danych innych niż SQL Server 2005 i SQL Server 2008.  
  
 Tematy w tej sekcji opisano właściwości i funkcji w magazynie wystąpień przepływu pracy SQL i dostarczać szczegółowe informacje na temat konfigurowania magazynu.  
  
 Windows Server AppFabric udostępnia własne wystąpienie magazynu i narzędziami uproszczenie konfiguracji i użycia w magazynie wystąpień. Aby uzyskać więcej informacji, zobacz zobacz [sklepu wystąpienia sieci szkieletowej dla systemu Windows Server](http://go.microsoft.com/fwlink/?LinkId=201201). Aby uzyskać więcej informacji o aplikacji sieci szkieletowej trwałości bazy danych SQL, zobacz [aplikacji sieci szkieletowej trwałości bazy danych SQL](http://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Właściwości magazynu wystąpień przepływu pracy SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Aktywacja wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Obsługa zapytań](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Rozszerzalność magazynu](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Zabezpieczenia](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [Baza danych stanów trwałych programu SQL Server](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości](http://go.microsoft.com/fwlink/?LinkID=177735)
