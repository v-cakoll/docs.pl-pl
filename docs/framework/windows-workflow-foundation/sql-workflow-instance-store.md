---
title: Magazyn wystąpień przepływu pracy SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 1764017369e82cfbed38be06b4a36847576b5fc0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837639"
---
# <a name="sql-workflow-instance-store"></a>Magazyn wystąpień przepływu pracy SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] jest dostarczany z magazynem wystąpień przepływu pracy SQL, który umożliwia przepływom pracy utrwalanie informacji o stanie wystąpień przepływu pracy w bazie danych SQL Server 2005 lub SQL Server 2008. Ta funkcja jest zaimplementowana głównie w formie klasy <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, która pochodzi z klasy abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> struktury trwałości. Funkcja magazynu wystąpień przepływu pracy SQL stanowi dostawcę trwałości SQL, który jest konkretną implementacją interfejsu API trwałości, którego host używa do wysyłania poleceń trwałości do magazynu.  
  
 Magazyn wystąpień przepływu pracy SQL obsługuje zarówno samohostowane przepływy pracy, jak i usługi przepływu pracy, które używają <xref:System.Activities.WorkflowApplication> lub <xref:System.ServiceModel.WorkflowServiceHost>, jak również usług hostowanych w programie przy użyciu <xref:System.ServiceModel.WorkflowServiceHost>. Funkcję magazynu wystąpień przepływu pracy SQL można skonfigurować programowo dla usług samoobsługowych przy użyciu modelu obiektów uwidocznionego przez funkcję. Tę funkcję można skonfigurować dla usług hostowanych przez <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu modelu obiektów, a także przy użyciu pliku konfiguracyjnego XML.  
  
 Funkcja magazynu wystąpień przepływu pracy SQL (Klasa**obiekt SqlWorkflowInstanceStore** ) nie implementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> i w związku z tym nie oferuje trwałości w przypadku trwałych usług WCF innych niż przepływ pracy. Nie implementuje również <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>, w związku z czym nie oferuje obsługi nietrwałości dla przepływów pracy 3. x. Funkcja obsługuje trwałość tylko dla przepływów pracy WF 4,0 (i nowszych) oraz usług Workflow Services. Ta funkcja nie obsługuje również żadnych baz danych innych niż SQL Server 2005 i SQL Server 2008.  
  
 W tematach w tej sekcji opisano właściwości i funkcje magazynu wystąpień przepływu pracy SQL i przedstawiono szczegółowe informacje na temat konfigurowania sklepu.  
  
 Sieć szkieletowa aplikacji systemu Windows Server zapewnia własne magazyny wystąpień i narzędzia upraszczające konfigurację i użycie magazynu wystąpień. Aby uzyskać więcej informacji, zobacz [Magazyn wystąpień aplikacji Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)). Aby uzyskać więcej informacji na temat usługi App Fabric SQL Server trwałości, zobacz [baza danych usługi App fabric SQL Server trwałości](https://docs.microsoft.com/previous-versions/appfabric/ee790819(v=azure.10))  
  
## <a name="in-this-section"></a>W tej sekcji  
  
- [Właściwości magazynu wystąpień przepływu pracy SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Aktywacja wystąpienia](instance-activation.md)  
  
- [Obsługa zapytań](support-for-queries.md)  
  
- [Rozszerzalność magazynu](store-extensibility.md)  
  
- [Security](security.md)  
  
- [Baza danych stanów trwałych programu SQL Server](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Zobacz także

- [Próbki trwałości](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
