---
title: IHostTask::GetPriority — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
ms.openlocfilehash: 6c33fa6d2e6cb09f013c5334461e61235db549f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121422"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="8465c-102">IHostTask::GetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="8465c-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="8465c-103">Pobiera poziom priorytetu wątku zadania reprezentowanego przez bieżące wystąpienie [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8465c-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8465c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8465c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8465c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8465c-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="8465c-106">określoną Wskaźnik do liczby całkowitej, która wskazuje poziom priorytetu wątku zadania reprezentowanego przez bieżące wystąpienie `IHostTask`.</span><span class="sxs-lookup"><span data-stu-id="8465c-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8465c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8465c-107">Return Value</span></span>  
  
|<span data-ttu-id="8465c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8465c-108">HRESULT</span></span>|<span data-ttu-id="8465c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="8465c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8465c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8465c-110">S_OK</span></span>|<span data-ttu-id="8465c-111">`GetPriority` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="8465c-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="8465c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8465c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8465c-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8465c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8465c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8465c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8465c-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8465c-115">The call timed out.</span></span>|  
|<span data-ttu-id="8465c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8465c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8465c-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8465c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8465c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8465c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8465c-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8465c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8465c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8465c-120">E_FAIL</span></span>|<span data-ttu-id="8465c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8465c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8465c-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="8465c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8465c-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8465c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8465c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8465c-124">Remarks</span></span>  
 <span data-ttu-id="8465c-125">Wartości poziomu priorytetu wątku są definiowane przez funkcję `SetThreadPriority` Win32.</span><span class="sxs-lookup"><span data-stu-id="8465c-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8465c-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8465c-126">Requirements</span></span>  
 <span data-ttu-id="8465c-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8465c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8465c-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8465c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8465c-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8465c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8465c-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8465c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8465c-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8465c-131">See also</span></span>

- [<span data-ttu-id="8465c-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8465c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="8465c-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8465c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="8465c-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="8465c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="8465c-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8465c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
