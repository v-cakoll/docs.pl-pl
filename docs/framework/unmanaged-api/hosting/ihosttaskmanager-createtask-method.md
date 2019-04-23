---
title: IHostTaskManager::CreateTask — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eddb11ab56bae5243ea7d00614090bbfe774f71
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096384"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="88997-102">IHostTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="88997-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="88997-103">Żądania, że host Utwórz nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="88997-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88997-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88997-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88997-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88997-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="88997-106">[in] Żądany rozmiar w bajtach stosu żądanego lub 0 (zero) domyślny rozmiar.</span><span class="sxs-lookup"><span data-stu-id="88997-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="88997-107">[in] Wskaźnik do funkcji zadanie jest zadaniem do wykonania.</span><span class="sxs-lookup"><span data-stu-id="88997-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="88997-108">[in] Wskaźnik do danych użytkownika, który zostanie przekazany do funkcji, lub wartość null, jeśli funkcja nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="88997-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="88997-109">[out] Wskaźnik na adres [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia utworzone przez hosta, lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="88997-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="88997-110">Zadanie pozostanie w stanie wstrzymania, aż jawnie jest uruchomione przez wywołanie do [ihosttask::Start —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="88997-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88997-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="88997-111">Return Value</span></span>  
  
|<span data-ttu-id="88997-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88997-112">HRESULT</span></span>|<span data-ttu-id="88997-113">Opis</span><span class="sxs-lookup"><span data-stu-id="88997-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88997-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="88997-114">S_OK</span></span>|<span data-ttu-id="88997-115">`CreateTask` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="88997-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="88997-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="88997-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="88997-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="88997-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="88997-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="88997-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="88997-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="88997-119">The call timed out.</span></span>|  
|<span data-ttu-id="88997-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="88997-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="88997-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="88997-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="88997-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="88997-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="88997-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="88997-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="88997-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="88997-124">E_FAIL</span></span>|<span data-ttu-id="88997-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="88997-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="88997-126">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="88997-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="88997-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="88997-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="88997-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="88997-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="88997-129">Za mało dostępnej pamięci na utworzyć żądanego zadania.</span><span class="sxs-lookup"><span data-stu-id="88997-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88997-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88997-130">Remarks</span></span>  
 <span data-ttu-id="88997-131">CLR wywołuje `CreateTask` na żądanie, że host Utwórz nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="88997-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="88997-132">Host zwraca wskaźnik interfejsu do `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="88997-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="88997-133">Zwrócone zadanie musi pozostać zawieszone, aż jawnie jest uruchomione przez wywołanie do `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="88997-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88997-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88997-134">Requirements</span></span>  
 <span data-ttu-id="88997-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88997-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88997-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88997-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="88997-137">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88997-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88997-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88997-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88997-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88997-139">See also</span></span>

- [<span data-ttu-id="88997-140">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="88997-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="88997-141">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="88997-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="88997-142">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="88997-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="88997-143">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="88997-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
