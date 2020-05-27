---
title: IHostGCManager::ThreadIsBlockingForSuspension — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 0417a4acc0f4f39d8254eb5d5df3b3e690921a8a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804827"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="dba03-102">IHostGCManager::ThreadIsBlockingForSuspension — Metoda</span><span class="sxs-lookup"><span data-stu-id="dba03-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="dba03-103">Powiadamia hosta, że wątek, z którego wykonano wywołanie metody, ma zablokować na wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dba03-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dba03-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dba03-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dba03-105">Return Value</span></span>  
  
|<span data-ttu-id="dba03-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dba03-106">HRESULT</span></span>|<span data-ttu-id="dba03-107">Opis</span><span class="sxs-lookup"><span data-stu-id="dba03-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dba03-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="dba03-108">S_OK</span></span>|<span data-ttu-id="dba03-109">`ThreadIsBlockingForSuspension`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="dba03-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="dba03-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dba03-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dba03-111">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dba03-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dba03-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dba03-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dba03-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="dba03-113">The call timed out.</span></span>|  
|<span data-ttu-id="dba03-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dba03-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dba03-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="dba03-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dba03-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dba03-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dba03-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="dba03-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dba03-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dba03-118">E_FAIL</span></span>|<span data-ttu-id="dba03-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="dba03-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dba03-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="dba03-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dba03-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dba03-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba03-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dba03-122">Remarks</span></span>  
 <span data-ttu-id="dba03-123">Środowisko CLR zazwyczaj wywołuje `ThreadIsBlockForSuspension` metodę w przygotowaniu do wyrzucania elementów bezużytecznych, aby umożliwić hostowi ponowne zaplanowanie wątku dla niezarządzanych zadań.</span><span class="sxs-lookup"><span data-stu-id="dba03-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dba03-124">Host może zmienić harmonogram zadań dopiero po wywołaniu `ThreadIsBlockingForSuspension` .</span><span class="sxs-lookup"><span data-stu-id="dba03-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="dba03-125">Po [SuspensionStarting —](ihostgcmanager-suspensionstarting-method.md)wywołań środowiska uruchomieniowego hosta nie może ponownie zaplanować zadania.</span><span class="sxs-lookup"><span data-stu-id="dba03-125">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba03-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dba03-126">Requirements</span></span>  
 <span data-ttu-id="dba03-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba03-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba03-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dba03-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dba03-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dba03-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dba03-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba03-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba03-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dba03-131">See also</span></span>

- [<span data-ttu-id="dba03-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dba03-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="dba03-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dba03-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="dba03-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="dba03-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="dba03-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dba03-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="dba03-136">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dba03-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
