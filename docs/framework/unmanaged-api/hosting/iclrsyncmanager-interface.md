---
title: "ICLRSyncManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5406a7a2912554552697c11fd7aa7a2c0e643fa0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="e5780-102">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e5780-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="e5780-103">Definiuje metody, które umożliwiają hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="e5780-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5780-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e5780-104">Methods</span></span>  
  
|<span data-ttu-id="e5780-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5780-105">Method</span></span>|<span data-ttu-id="e5780-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e5780-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5780-107">CreateRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="e5780-107">CreateRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="e5780-108">Żądania, które iteratora hosta na służy do określania zestawu zadań oczekujących na blokadę zapisu czytnika utworzyć środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="e5780-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="e5780-109">DeleteRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="e5780-109">DeleteRWLockOwnerIterator Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="e5780-110">Żąda, że środowisko CLR zniszczyć iterację, która została utworzona przez wywołanie do `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="e5780-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="e5780-111">GetMonitorOwner, metoda</span><span class="sxs-lookup"><span data-stu-id="e5780-111">GetMonitorOwner Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="e5780-112">Pobiera zadanie, który jest właścicielem określony monitor.</span><span class="sxs-lookup"><span data-stu-id="e5780-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="e5780-113">GetRWLockOwnerNext, metoda</span><span class="sxs-lookup"><span data-stu-id="e5780-113">GetRWLockOwnerNext Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="e5780-114">Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="e5780-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e5780-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5780-115">Requirements</span></span>  
 <span data-ttu-id="e5780-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5780-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5780-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e5780-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e5780-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5780-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5780-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5780-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5780-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5780-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="e5780-121">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5780-121">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="e5780-122">Zarządzana i niezarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="e5780-122">Managed and Unmanaged Threading</span></span>](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [<span data-ttu-id="e5780-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e5780-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
