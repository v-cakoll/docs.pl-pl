---
title: Zabezpieczenia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17b77293d9a12fd3720fc54cb6c17a28a8c6ed0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security"></a><span data-ttu-id="264d9-102">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="264d9-102">Security</span></span>
<span data-ttu-id="264d9-103">W magazynie wystąpień przepływu pracy SQL są używane następujące role zabezpieczeń bazy danych do bezpieczny dostęp do informacji o stanie wystąpienie w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="264d9-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
-   <span data-ttu-id="264d9-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span><span class="sxs-lookup"><span data-stu-id="264d9-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="264d9-105">Ta rola zapoznał się oraz publicznie do zapisu i wykonywania prawa do przechowywane procedur, które nie są związane z tworzeniem, ładowania i zapisywania wystąpień.</span><span class="sxs-lookup"><span data-stu-id="264d9-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
-   <span data-ttu-id="264d9-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span><span class="sxs-lookup"><span data-stu-id="264d9-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="264d9-107">Ta rola ma dostęp tylko do odczytu do widoków publicznych.</span><span class="sxs-lookup"><span data-stu-id="264d9-107">This role has read-only access to public views.</span></span>  
  
-   <span data-ttu-id="264d9-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="264d9-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="264d9-109">Ta rola ma prawa wykonywania na procedury składowane, które są zaangażowane w procesie aktywacji wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="264d9-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="264d9-110">Aby uzyskać więcej informacji o wystąpieniu aktywacji, zobacz [aktywacji wystąpienia](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span><span class="sxs-lookup"><span data-stu-id="264d9-110">For more information about instance activation, see [Instance Activation](../../../docs/framework/windows-workflow-foundation/instance-activation.md).</span></span> <span data-ttu-id="264d9-111">Konto użytkownika, którego rodzajowego hosta (takich jak przepływ pracy usługi zarządzania [!INCLUDE[dublin](../../../includes/dublin-md.md)]) uruchamia powinni zostać dodani do tej roli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="264d9-111">The user account under which a generic host (such as the Workflow Management Service of [!INCLUDE[dublin](../../../includes/dublin-md.md)]) runs should be added to this database role.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="264d9-112">zabezpieczenia dla magazynów trwałości z systemu Windows Server AppFabric, zobacz [konfiguracji zabezpieczeń dla magazynów trwałości w aplikacji sieci szkieletowej](http://go.microsoft.com/fwlink/?LinkId=201208)</span><span class="sxs-lookup"><span data-stu-id="264d9-112"> security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](http://go.microsoft.com/fwlink/?LinkId=201208)</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="264d9-113">Klient, który ma dostęp do danych wystąpienia w magazynie wystąpień ma dostęp do wszystkich innych wystąpień w tym samym magazynie wystąpień.</span><span class="sxs-lookup"><span data-stu-id="264d9-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="264d9-114">W magazynie wystąpień nie obsługuje określania uprawnień zabezpieczeń na poziomie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="264d9-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="264d9-115">Należy utworzyć osobne wystąpienie magazynów i mapowania różnych grup/Użytkownicy mają mieć dostęp do różnych magazynów.</span><span class="sxs-lookup"><span data-stu-id="264d9-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
