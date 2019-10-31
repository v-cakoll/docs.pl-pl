---
title: IHostTaskManager::GetCurrentTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: d1d6ddfe7834a1c6f22b9195042d32363d6ea6cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133041"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="933fe-102">IHostTaskManager::GetCurrentTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="933fe-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="933fe-103">Pobiera wskaźnik interfejsu do zadania, które jest aktualnie wykonywane w wątku systemu operacyjnego, z którego wykonano to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="933fe-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="933fe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="933fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="933fe-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="933fe-106">określoną Wskaźnik do adresu wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) , który reprezentuje aktualnie wykonywane zadanie lub wartość null, jeśli żadne zadanie nie jest aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="933fe-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="933fe-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="933fe-107">Return Value</span></span>  
  
|<span data-ttu-id="933fe-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="933fe-108">HRESULT</span></span>|<span data-ttu-id="933fe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="933fe-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="933fe-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="933fe-110">S_OK</span></span>|<span data-ttu-id="933fe-111">`GetCurrentTask` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="933fe-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="933fe-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="933fe-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="933fe-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="933fe-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="933fe-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="933fe-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="933fe-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="933fe-115">The call timed out.</span></span>|  
|<span data-ttu-id="933fe-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="933fe-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="933fe-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="933fe-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="933fe-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="933fe-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="933fe-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="933fe-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="933fe-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="933fe-120">E_FAIL</span></span>|<span data-ttu-id="933fe-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="933fe-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="933fe-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="933fe-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="933fe-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="933fe-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="933fe-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="933fe-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="933fe-125">`GetCurrentTask` został wywołany w wątku systemu operacyjnego poza kontrolą hosta.</span><span class="sxs-lookup"><span data-stu-id="933fe-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="933fe-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="933fe-126">Remarks</span></span>  
 <span data-ttu-id="933fe-127">Host może również ustawić wartość null dla parametru `pTask`, aby uniemożliwić zadanie, które nie zostało zainicjowane od wprowadzenia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="933fe-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933fe-128">Wymagania</span><span class="sxs-lookup"><span data-stu-id="933fe-128">Requirements</span></span>  
 <span data-ttu-id="933fe-129">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933fe-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933fe-130">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="933fe-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="933fe-131">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="933fe-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="933fe-132">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933fe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933fe-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="933fe-133">See also</span></span>

- [<span data-ttu-id="933fe-134">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="933fe-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="933fe-135">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="933fe-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="933fe-136">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="933fe-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="933fe-137">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="933fe-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
