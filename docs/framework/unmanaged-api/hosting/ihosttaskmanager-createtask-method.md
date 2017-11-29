---
title: "IHostTaskManager::CreateTask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ba71fcd35b16654ab67db3f657f7821c23b702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="8f636-102">IHostTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f636-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="8f636-103">Żądania, hosta utworzyć nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="8f636-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f636-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f636-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [in]  DWORD stacksize,   
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f636-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f636-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="8f636-106">[in] Żądany rozmiar w bajtach żądanego stosu lub domyślny rozmiar 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="8f636-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="8f636-107">[in] Wskaźnik do funkcji jest zadanie do wykonania.</span><span class="sxs-lookup"><span data-stu-id="8f636-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="8f636-108">[in] Wskaźnik do danych użytkownika, które mają być przekazane do funkcji lub wartość null, jeśli funkcja nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8f636-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="8f636-109">[out] Wskaźnik do adresu [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia utworzone przez hosta lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="8f636-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="8f636-110">Zadanie pozostanie w stanie wstrzymania po jawnie jest uruchomiony przez wywołanie do [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="8f636-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f636-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8f636-111">Return Value</span></span>  
  
|<span data-ttu-id="8f636-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f636-112">HRESULT</span></span>|<span data-ttu-id="8f636-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8f636-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f636-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f636-114">S_OK</span></span>|<span data-ttu-id="8f636-115">`CreateTask`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8f636-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="8f636-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f636-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f636-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f636-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f636-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f636-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f636-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8f636-119">The call timed out.</span></span>|  
|<span data-ttu-id="8f636-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f636-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f636-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8f636-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f636-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f636-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f636-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8f636-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f636-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f636-124">E_FAIL</span></span>|<span data-ttu-id="8f636-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8f636-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f636-126">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8f636-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f636-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8f636-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f636-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8f636-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8f636-129">Za mało pamięci nie była dostępna, można utworzyć żądanego zadania.</span><span class="sxs-lookup"><span data-stu-id="8f636-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f636-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f636-130">Remarks</span></span>  
 <span data-ttu-id="8f636-131">Wywołania CLR `CreateTask` na żądanie, że host utworzyć nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="8f636-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="8f636-132">Host zwraca wskaźnika interfejsu do `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8f636-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="8f636-133">Zadanie zwrócone musi pozostać zawieszone po jawnie jest uruchomiony przez wywołanie do `IHostTask::Start`.</span><span class="sxs-lookup"><span data-stu-id="8f636-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f636-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f636-134">Requirements</span></span>  
 <span data-ttu-id="8f636-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f636-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f636-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8f636-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f636-137">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8f636-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f636-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f636-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f636-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f636-139">See Also</span></span>  
 [<span data-ttu-id="8f636-140">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="8f636-140">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="8f636-141">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="8f636-141">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="8f636-142">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="8f636-142">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="8f636-143">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="8f636-143">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
