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
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178001"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="af8bb-102">IHostTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="af8bb-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="af8bb-103">Żąda, aby host utworzył nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="af8bb-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af8bb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af8bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af8bb-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="af8bb-106">[w] Żądany rozmiar w bajtach żądanego stosu lub 0 (zero) dla rozmiaru domyślnego.</span><span class="sxs-lookup"><span data-stu-id="af8bb-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="af8bb-107">[w] Wskaźnik do funkcji, której zadanie ma wykonać.</span><span class="sxs-lookup"><span data-stu-id="af8bb-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="af8bb-108">[w] Wskaźnik do danych użytkownika, które mają być przekazywane do funkcji lub null, jeśli funkcja nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="af8bb-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="af8bb-109">[na zewnątrz] Wskaźnik do adresu wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) utworzonego przez hosta lub null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="af8bb-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="af8bb-110">Zadanie pozostaje w stanie wstrzymanym, dopóki nie zostanie jawnie rozpoczęte przez wywołanie [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="af8bb-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af8bb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="af8bb-111">Return Value</span></span>  
  
|<span data-ttu-id="af8bb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af8bb-112">HRESULT</span></span>|<span data-ttu-id="af8bb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="af8bb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af8bb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="af8bb-114">S_OK</span></span>|<span data-ttu-id="af8bb-115">`CreateTask`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="af8bb-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="af8bb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af8bb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af8bb-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="af8bb-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af8bb-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af8bb-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af8bb-119">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="af8bb-119">The call timed out.</span></span>|  
|<span data-ttu-id="af8bb-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af8bb-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af8bb-121">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="af8bb-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af8bb-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af8bb-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af8bb-123">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="af8bb-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af8bb-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="af8bb-124">E_FAIL</span></span>|<span data-ttu-id="af8bb-125">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="af8bb-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af8bb-126">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="af8bb-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af8bb-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="af8bb-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="af8bb-128">E_outofmemory</span><span class="sxs-lookup"><span data-stu-id="af8bb-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="af8bb-129">Za mało pamięci było dostępne do utworzenia żądanego zadania.</span><span class="sxs-lookup"><span data-stu-id="af8bb-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8bb-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af8bb-130">Remarks</span></span>  
 <span data-ttu-id="af8bb-131">Clr wywołuje `CreateTask` żądanie, aby host utworzyć nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="af8bb-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="af8bb-132">Host zwraca wskaźnik interfejsu `IHostTask` do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="af8bb-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="af8bb-133">Zwrócone zadanie musi pozostać zawieszone, dopóki nie `IHostTask::Start`zostanie jawnie rozpoczęte przez wywołanie .</span><span class="sxs-lookup"><span data-stu-id="af8bb-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8bb-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af8bb-134">Requirements</span></span>  
 <span data-ttu-id="af8bb-135">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8bb-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8bb-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af8bb-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af8bb-137">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af8bb-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af8bb-138">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8bb-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8bb-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af8bb-139">See also</span></span>

- [<span data-ttu-id="af8bb-140">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="af8bb-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="af8bb-141">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="af8bb-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="af8bb-142">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="af8bb-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="af8bb-143">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="af8bb-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
