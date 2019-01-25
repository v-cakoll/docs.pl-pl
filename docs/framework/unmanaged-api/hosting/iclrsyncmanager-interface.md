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
ms.openlocfilehash: 4b949466c5557415ec06bac601380675beed7fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549866"
---
# <a name="iclrsyncmanager-interface"></a><span data-ttu-id="42872-102">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="42872-102">ICLRSyncManager Interface</span></span>
<span data-ttu-id="42872-103">Definiuje metody, które umożliwiają hosta, aby uzyskać informacje o żądanych zadań i wykrył zakleszczenie w jego implementacja synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="42872-103">Defines methods that allow the host to get information about requested tasks and to detect deadlocks in its synchronization implementation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42872-104">Metody</span><span class="sxs-lookup"><span data-stu-id="42872-104">Methods</span></span>  
  
|<span data-ttu-id="42872-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="42872-105">Method</span></span>|<span data-ttu-id="42872-106">Opis</span><span class="sxs-lookup"><span data-stu-id="42872-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42872-107">CreateRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="42872-107">CreateRWLockOwnerIterator Method</span></span>](iclrsyncmanager-createrwlockowneriterator-method.md)|<span data-ttu-id="42872-108">Żądania, które środowisko uruchomieniowe języka wspólnego (CLR) Utwórz iterator dla hosta na potrzeby określania zestawu zadań, oczekiwania na blokadę zapisu czytnika.</span><span class="sxs-lookup"><span data-stu-id="42872-108">Requests that the common language runtime (CLR) create an iterator for the host to use to determine the set of tasks waiting on a reader-writer lock.</span></span>|  
|[<span data-ttu-id="42872-109">DeleteRWLockOwnerIterator, metoda</span><span class="sxs-lookup"><span data-stu-id="42872-109">DeleteRWLockOwnerIterator Method</span></span>](iclrsyncmanager-deleterwlockowneriterator-method.md)|<span data-ttu-id="42872-110">Żądania, że środowisko CLR zniszczyć iterator, który został utworzony przez wywołanie `CreateRWLockOwnerIterator`.</span><span class="sxs-lookup"><span data-stu-id="42872-110">Requests that the CLR destroy an iterator that was created by a call to `CreateRWLockOwnerIterator`.</span></span>|  
|[<span data-ttu-id="42872-111">GetMonitorOwner, metoda</span><span class="sxs-lookup"><span data-stu-id="42872-111">GetMonitorOwner Method</span></span>](iclrsyncmanager-getmonitorowner-method.md)|<span data-ttu-id="42872-112">Pobiera zadanie, które jest właścicielem określony monitor.</span><span class="sxs-lookup"><span data-stu-id="42872-112">Gets the task that owns the specified monitor.</span></span>|  
|[<span data-ttu-id="42872-113">GetRWLockOwnerNext, metoda</span><span class="sxs-lookup"><span data-stu-id="42872-113">GetRWLockOwnerNext Method</span></span>](iclrsyncmanager-getrwlockownernext-method.md)|<span data-ttu-id="42872-114">Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.</span><span class="sxs-lookup"><span data-stu-id="42872-114">Gets the next task that is waiting on the current reader-writer lock.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="42872-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42872-115">Requirements</span></span>  
 <span data-ttu-id="42872-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42872-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42872-117">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="42872-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="42872-118">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="42872-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42872-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42872-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42872-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42872-120">See also</span></span>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="42872-121">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="42872-121">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <span data-ttu-id="42872-122">[Zarządzana i niezarządzana wątkowość](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="42872-122">[Managed and Unmanaged Threading](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))</span></span>
- [<span data-ttu-id="42872-123">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="42872-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
