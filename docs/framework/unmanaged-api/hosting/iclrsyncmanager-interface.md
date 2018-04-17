---
title: ICLRSyncManager — Interfejs
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ICLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager
helpviewer_keywords:
- ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17a1e3073713b54cb7a68e6ba3ef2562d4fbcaeb
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="de27b-102">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="de27b-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="de27b-103">Definiuje metody, które umożliwiają hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="de27b-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de27b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="de27b-104">Methods</span></span>  
  
|<span data-ttu-id="de27b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="de27b-105">Method</span></span>|<span data-ttu-id="de27b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="de27b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de27b-107">CreateRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="de27b-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="de27b-108">Żądania, które iteratora hosta na służy do określania zestawu zadań oczekujących na blokadę zapisu czytnika utworzyć środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="de27b-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="de27b-109">DeleteRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="de27b-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="de27b-110">Żąda, że środowisko CLR zniszczyć iterację, która została utworzona przez wywołanie do `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="de27b-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="de27b-111">GetMonitorOwner, metoda</span><span class="sxs-lookup"><span data-stu-id="de27b-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="de27b-112">Pobiera zadanie, który jest właścicielem określony monitor.</span><span class="sxs-lookup"><span data-stu-id="de27b-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="de27b-113">GetRWLockOwnerNext, metoda</span><span class="sxs-lookup"><span data-stu-id="de27b-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="de27b-114">Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="de27b-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="de27b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de27b-115">Requirements</span></span>  
 <span data-ttu-id="de27b-116">**Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de27b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de27b-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de27b-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de27b-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de27b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de27b-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de27b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de27b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de27b-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="de27b-121">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="de27b-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="de27b-122">[Zarządzana i niezarządzana wątkowość](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de27b-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="de27b-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="de27b-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
