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
# <a name="sql-workflow-instance-store"></a><span data-ttu-id="c6e97-102">Magazyn wystąpienia przepływu pracy SQL</span><span class="sxs-lookup"><span data-stu-id="c6e97-102">SQL Workflow Instance Store</span></span>
<span data-ttu-id="c6e97-103">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Jest dostarczany z SQL magazyn wystąpienia przepływu pracy, dzięki czemu przepływy pracy, aby zachować informacje o stanie dotyczące wystąpienia przepływu pracy w bazie danych programu SQL Server 2005 lub SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c6e97-103">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ships with the SQL Workflow Instance Store, which allows workflows to persist state information about workflow instances in a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="c6e97-104">Ta funkcja jest głównie zaimplementowana w formie <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> klasy, która pochodzi z klasy abstrakcyjnej <xref:System.Runtime.DurableInstancing.InstanceStore> klasy framework trwałości.</span><span class="sxs-lookup"><span data-stu-id="c6e97-104">This feature is primarily implemented in the form of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> class, which derives from the abstract <xref:System.Runtime.DurableInstancing.InstanceStore> class of the persistence framework.</span></span> <span data-ttu-id="c6e97-105">Funkcja magazynu wystąpienia przepływu pracy SQL stanowi SQL dostawcy trwałości, który jest konkretną implementację trwałości interfejsu API używany przez hosta do wysyłania polecenia trwałości w magazynie.</span><span class="sxs-lookup"><span data-stu-id="c6e97-105">The SQL Workflow Instance Store feature constitutes a SQL persistence provider, which is a concrete implementation of the persistence API that a host uses to send persistence commands to the store.</span></span>  
  
 <span data-ttu-id="c6e97-106">W magazynie wystąpień przepływu pracy SQL obsługuje zarówno siebie przepływy pracy lub usług przepływu pracy, które używają <xref:System.Activities.WorkflowApplication> lub <xref:System.ServiceModel.WorkflowServiceHost> oraz usług hostowanych w trybie <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="c6e97-106">The SQL Workflow Instance Store supports both self-hosted workflows or workflow services that use <xref:System.Activities.WorkflowApplication> or <xref:System.ServiceModel.WorkflowServiceHost> as well as services hosted in WAS using <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="c6e97-107">Funkcja magazynu wystąpienia przepływu pracy SQL dla usług hostowania samoobsługowego można skonfigurować programowo przy użyciu model obiektowy udostępniany przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="c6e97-107">You can configure the SQL Workflow Instance Store feature for self-hosted services programmatically by using the object model exposed by the feature.</span></span> <span data-ttu-id="c6e97-108">Można skonfigurować tej funkcji dla usług hostowanych na <xref:System.ServiceModel.WorkflowServiceHost> programowo przy użyciu modelu obiektu, a także za pomocą pliku konfiguracji XML.</span><span class="sxs-lookup"><span data-stu-id="c6e97-108">You can configure this feature for services hosted by <xref:System.ServiceModel.WorkflowServiceHost> both programmatically by using the object model and also by using an XML configuration file.</span></span>  
  
 <span data-ttu-id="c6e97-109">Funkcja magazynu wystąpienia przepływu pracy SQL (**SqlWorkflowInstanceStore** klasy) nie implementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> i dlatego nie oferuje obsługę trwałości trwałe usługi WCF bez przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6e97-109">The SQL Workflow Instance Store feature (**SqlWorkflowInstanceStore** class) does not implement <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> and hence does not offer persistence support for durable non-workflow WCF services.</span></span> <span data-ttu-id="c6e97-110">Również nie implementuje on <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> i dlatego nie oferuje pomocy trwałości dla przepływów pracy 3.x.</span><span class="sxs-lookup"><span data-stu-id="c6e97-110">It also does not implement <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> and hence does not offer persistence support for 3.x workflows.</span></span> <span data-ttu-id="c6e97-111">Gdy funkcja obsługuje przepływy pracy trwałości tylko WF 4.0 (i nowszych) i usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="c6e97-111">The feature supports persistence for only WF 4.0 (and later) workflows and workflow services.</span></span> <span data-ttu-id="c6e97-112">Funkcja nie obsługuje również żadnych baz danych innych niż SQL Server 2005 i SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="c6e97-112">The feature also does not support any databases other than SQL Server 2005 and SQL Server 2008.</span></span>  
  
 <span data-ttu-id="c6e97-113">Tematy w tej sekcji opisano właściwości i funkcji w magazynie wystąpień przepływu pracy SQL i dostarczać szczegółowe informacje na temat konfigurowania magazynu.</span><span class="sxs-lookup"><span data-stu-id="c6e97-113">The topics in this section describe properties and features of the SQL Workflow Instance Store and provide you with details on configuring the store.</span></span>  
  
 <span data-ttu-id="c6e97-114">Windows Server AppFabric udostępnia własne wystąpienie magazynu i narzędziami uproszczenie konfiguracji i użycia w magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="c6e97-114">Windows Server App Fabric provides its own instance store and tooling to simplify the configuration and use of the instance store.</span></span> <span data-ttu-id="c6e97-115">Aby uzyskać więcej informacji, zobacz zobacz [sklepu wystąpienia sieci szkieletowej dla systemu Windows Server](http://go.microsoft.com/fwlink/?LinkId=201201).</span><span class="sxs-lookup"><span data-stu-id="c6e97-115">For more information, see see [Windows Server App Fabric Instance Store](http://go.microsoft.com/fwlink/?LinkId=201201).</span></span> <span data-ttu-id="c6e97-116">Aby uzyskać więcej informacji o aplikacji sieci szkieletowej trwałości bazy danych SQL, zobacz [aplikacji sieci szkieletowej trwałości bazy danych SQL](http://go.microsoft.com/fwlink/?LinkId=201202)</span><span class="sxs-lookup"><span data-stu-id="c6e97-116">For more information about the App Fabric SQL Server Persistence Database see [App Fabric SQL Server Persistence Database](http://go.microsoft.com/fwlink/?LinkId=201202)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c6e97-117">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="c6e97-117">In This Section</span></span>  
  
-   [<span data-ttu-id="c6e97-118">Właściwości magazynu wystąpień przepływu pracy SQL</span><span class="sxs-lookup"><span data-stu-id="c6e97-118">Properties of SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="c6e97-119">Instrukcje: Włączanie stanów trwałych programu SQL dla przepływów pracy i usług przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c6e97-119">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [<span data-ttu-id="c6e97-120">Aktywacja wystąpienia</span><span class="sxs-lookup"><span data-stu-id="c6e97-120">Instance Activation</span></span>](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [<span data-ttu-id="c6e97-121">Obsługa zapytań</span><span class="sxs-lookup"><span data-stu-id="c6e97-121">Support for Queries</span></span>](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [<span data-ttu-id="c6e97-122">Rozszerzalność magazynu</span><span class="sxs-lookup"><span data-stu-id="c6e97-122">Store Extensibility</span></span>](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [<span data-ttu-id="c6e97-123">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="c6e97-123">Security</span></span>](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [<span data-ttu-id="c6e97-124">Baza danych stanów trwałych programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6e97-124">SQL Server Persistence Database</span></span>](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6e97-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6e97-125">See Also</span></span>  
 [<span data-ttu-id="c6e97-126">Przykłady trwałości</span><span class="sxs-lookup"><span data-stu-id="c6e97-126">Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkID=177735)
