---
title: ICLRSyncManager — Interfejs
ms.date: 03/30/2017
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
ms.openlocfilehash: 1b87ccc3d6c3e957d0384499048032e35247093a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="f56c7-102">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f56c7-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="f56c7-103">Definiuje metody, które umożliwiają hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="f56c7-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f56c7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f56c7-104">Methods</span></span>  
  
|<span data-ttu-id="f56c7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f56c7-105">Method</span></span>|<span data-ttu-id="f56c7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f56c7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f56c7-107">CreateRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="f56c7-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="f56c7-108">Żądania, które iteratora hosta na służy do określania zestawu zadań oczekujących na blokadę zapisu czytnika utworzyć środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f56c7-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="f56c7-109">DeleteRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="f56c7-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="f56c7-110">Żąda, że środowisko CLR zniszczyć iterację, która została utworzona przez wywołanie do `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="f56c7-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="f56c7-111">GetMonitorOwner, metoda</span><span class="sxs-lookup"><span data-stu-id="f56c7-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="f56c7-112">Pobiera zadanie, który jest właścicielem określony monitor.</span><span class="sxs-lookup"><span data-stu-id="f56c7-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="f56c7-113">GetRWLockOwnerNext, metoda</span><span class="sxs-lookup"><span data-stu-id="f56c7-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="f56c7-114">Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="f56c7-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f56c7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f56c7-115">Requirements</span></span>  
 <span data-ttu-id="f56c7-116">**Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f56c7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f56c7-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f56c7-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f56c7-118">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f56c7-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f56c7-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f56c7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f56c7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f56c7-120">See Also</span></span>  
 <xref:System.Threading.Thread>  
 [<span data-ttu-id="f56c7-121">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f56c7-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)  
 <span data-ttu-id="f56c7-122">[Zarządzana i niezarządzana wątkowość](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f56c7-122">[Managed and Unmanaged Threading](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))</span></span>  
 [<span data-ttu-id="f56c7-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f56c7-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
