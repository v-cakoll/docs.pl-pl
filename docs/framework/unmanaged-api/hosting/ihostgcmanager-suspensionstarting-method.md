---
title: IHostGCManager::SuspensionStarting — Metoda
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionStarting
helpviewer_keywords:
- SuspensionStarting method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionStarting method [.NET Framework hosting]
ms.assetid: c381f524-94cf-4fa2-9298-50f847a03431
topic_type:
- apiref
ms.openlocfilehash: f2b4028c78daf266e4ffecd86e6b0b30b9607d5b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804817"
---
# <a name="ihostgcmanagersuspensionstarting-method"></a><span data-ttu-id="ef8f2-102">IHostGCManager::SuspensionStarting — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef8f2-102">IHostGCManager::SuspensionStarting Method</span></span>
<span data-ttu-id="ef8f2-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) wstrzymuje wykonywanie zadań, aby wykonać wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-103">Notifies the host that the common language runtime (CLR) is suspending execution of tasks, to perform a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef8f2-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ef8f2-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ef8f2-105">Return Value</span></span>  
  
|<span data-ttu-id="ef8f2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef8f2-106">HRESULT</span></span>|<span data-ttu-id="ef8f2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef8f2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef8f2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef8f2-108">S_OK</span></span>|<span data-ttu-id="ef8f2-109">`SuspensionStarting`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-109">`SuspensionStarting` returned successfully.</span></span>|  
|<span data-ttu-id="ef8f2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ef8f2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ef8f2-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ef8f2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ef8f2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ef8f2-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-113">The call timed out.</span></span>|  
|<span data-ttu-id="ef8f2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ef8f2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ef8f2-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ef8f2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ef8f2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ef8f2-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ef8f2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ef8f2-118">E_FAIL</span></span>|<span data-ttu-id="ef8f2-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ef8f2-120">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ef8f2-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef8f2-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef8f2-122">Remarks</span></span>  
 <span data-ttu-id="ef8f2-123">Środowisko CLR wywołuje, `SuspensionStarting` aby poinformować hosta, że występuje wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-123">The CLR calls `SuspensionStarting` to inform the host that garbage collection is occurring.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef8f2-124">Nie należy ponownie zaplanować tego zadania.</span><span class="sxs-lookup"><span data-stu-id="ef8f2-124">Do not reschedule this task.</span></span> <span data-ttu-id="ef8f2-125">Host musi ponownie zaplanować zadanie, gdy zostanie wywołane [ThreadIsBlockingForSuspension —](ihostgcmanager-threadisblockingforsuspension-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ef8f2-125">The host must reschedule a task when [ThreadIsBlockingForSuspension](ihostgcmanager-threadisblockingforsuspension-method.md) is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8f2-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef8f2-126">Requirements</span></span>  
 <span data-ttu-id="ef8f2-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef8f2-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8f2-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ef8f2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef8f2-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef8f2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef8f2-130">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8f2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8f2-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef8f2-131">See also</span></span>

- [<span data-ttu-id="ef8f2-132">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8f2-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="ef8f2-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8f2-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="ef8f2-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8f2-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="ef8f2-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8f2-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="ef8f2-136">IHostGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ef8f2-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
