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
ms.openlocfilehash: 7079a915c0402df62afa5648317619af82c943b0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841987"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="44e8e-102">IHostTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="44e8e-102">IHostTaskManager::CreateTask Method</span></span>
<span data-ttu-id="44e8e-103">Żąda utworzenia nowego zadania przez hosta.</span><span class="sxs-lookup"><span data-stu-id="44e8e-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44e8e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44e8e-105">Parameters</span></span>  
 `stacksize`  
 <span data-ttu-id="44e8e-106">podczas Żądany rozmiar (w bajtach) żądanego stosu lub 0 (zero) dla rozmiaru domyślnego.</span><span class="sxs-lookup"><span data-stu-id="44e8e-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="44e8e-107">podczas Wskaźnik do funkcji, która ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="44e8e-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="44e8e-108">podczas Wskaźnik do danych użytkownika, który ma zostać przesłany do funkcji, lub wartość null, jeśli funkcja nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="44e8e-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="44e8e-109">określoną Wskaźnik do adresu wystąpienia [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) utworzonego przez hosta lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="44e8e-109">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="44e8e-110">Zadanie pozostaje w stanie wstrzymania, dopóki nie zostanie jawnie uruchomione przez wywołanie [IHostTask:: Start](ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="44e8e-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44e8e-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="44e8e-111">Return Value</span></span>  
  
|<span data-ttu-id="44e8e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="44e8e-112">HRESULT</span></span>|<span data-ttu-id="44e8e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="44e8e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="44e8e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="44e8e-114">S_OK</span></span>|<span data-ttu-id="44e8e-115">`CreateTask`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="44e8e-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="44e8e-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="44e8e-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="44e8e-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="44e8e-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="44e8e-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="44e8e-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="44e8e-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="44e8e-119">The call timed out.</span></span>|  
|<span data-ttu-id="44e8e-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="44e8e-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="44e8e-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="44e8e-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="44e8e-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="44e8e-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="44e8e-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="44e8e-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="44e8e-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="44e8e-124">E_FAIL</span></span>|<span data-ttu-id="44e8e-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="44e8e-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="44e8e-126">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="44e8e-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="44e8e-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="44e8e-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="44e8e-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="44e8e-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="44e8e-129">Za mało dostępnej pamięci, aby utworzyć żądane zadanie.</span><span class="sxs-lookup"><span data-stu-id="44e8e-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44e8e-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44e8e-130">Remarks</span></span>  
 <span data-ttu-id="44e8e-131">Środowisko CLR wywołuje `CreateTask` żądanie utworzenia nowego zadania przez hosta.</span><span class="sxs-lookup"><span data-stu-id="44e8e-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="44e8e-132">Host zwraca wskaźnik interfejsu do `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="44e8e-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="44e8e-133">Zwrócone zadanie musi pozostać zawieszone, dopóki nie zostanie jawnie uruchomione przez wywołanie `IHostTask::Start` .</span><span class="sxs-lookup"><span data-stu-id="44e8e-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e8e-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44e8e-134">Requirements</span></span>  
 <span data-ttu-id="44e8e-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44e8e-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44e8e-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="44e8e-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="44e8e-137">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="44e8e-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44e8e-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44e8e-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e8e-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44e8e-139">See also</span></span>

- [<span data-ttu-id="44e8e-140">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="44e8e-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="44e8e-141">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="44e8e-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="44e8e-142">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="44e8e-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="44e8e-143">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="44e8e-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
