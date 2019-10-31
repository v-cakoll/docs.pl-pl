---
title: ICLRTask::ExitTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: 3f6ccf2eb25e96e0f94c558fb642b153ae3472c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124898"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="5066f-102">ICLRTask::ExitTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="5066f-102">ICLRTask::ExitTask Method</span></span>
<span data-ttu-id="5066f-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o zakończeniu zadania reprezentowanego przez bieżące wystąpienie [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) i próbuje bezpiecznie zamknąć zadanie.</span><span class="sxs-lookup"><span data-stu-id="5066f-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5066f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5066f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5066f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5066f-105">Return Value</span></span>  
  
|<span data-ttu-id="5066f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5066f-106">HRESULT</span></span>|<span data-ttu-id="5066f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5066f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5066f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="5066f-108">S_OK</span></span>|<span data-ttu-id="5066f-109">`ExitTask` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="5066f-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="5066f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5066f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5066f-111">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5066f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5066f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5066f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5066f-113">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5066f-113">The call timed out.</span></span>|  
|<span data-ttu-id="5066f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5066f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5066f-115">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5066f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5066f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5066f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5066f-117">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5066f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5066f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5066f-118">E_FAIL</span></span>|<span data-ttu-id="5066f-119">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5066f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5066f-120">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="5066f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5066f-121">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5066f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5066f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5066f-122">Remarks</span></span>  
 <span data-ttu-id="5066f-123">`ExitTask` próbuje czyste zamknięcie zadania w sposób analogiczny do odłączania wątku z niezarządzanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5066f-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5066f-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5066f-124">Requirements</span></span>  
 <span data-ttu-id="5066f-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5066f-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5066f-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5066f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5066f-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5066f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5066f-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5066f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5066f-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5066f-129">See also</span></span>

- [<span data-ttu-id="5066f-130">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5066f-130">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5066f-131">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5066f-131">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5066f-132">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5066f-132">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5066f-133">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5066f-133">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
