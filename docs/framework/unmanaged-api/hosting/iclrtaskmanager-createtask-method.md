---
title: ICLRTaskManager::CreateTask — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89ea76d78431ae8833602588379d5150e473710
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938305"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="5f4e7-102">ICLRTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f4e7-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="5f4e7-103">Żądania jawnie, które tworzą nowe zadanie środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5f4e7-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f4e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5f4e7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f4e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f4e7-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="5f4e7-106">określoną Wskaźnik na adres nowo utworzonego [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5f4e7-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5f4e7-107">Return Value</span></span>  
  
|<span data-ttu-id="5f4e7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5f4e7-108">HRESULT</span></span>|<span data-ttu-id="5f4e7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="5f4e7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5f4e7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="5f4e7-110">S_OK</span></span>|<span data-ttu-id="5f4e7-111">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="5f4e7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5f4e7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5f4e7-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5f4e7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5f4e7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5f4e7-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-115">The call timed out.</span></span>|  
|<span data-ttu-id="5f4e7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5f4e7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5f4e7-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5f4e7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5f4e7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5f4e7-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5f4e7-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5f4e7-120">E_FAIL</span></span>|<span data-ttu-id="5f4e7-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5f4e7-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5f4e7-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5f4e7-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="5f4e7-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="5f4e7-125">Za mało dostępnej pamięci, aby przydzielić żądany zasób.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f4e7-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f4e7-126">Remarks</span></span>  
 <span data-ttu-id="5f4e7-127">Środowisko CLR tworzy nowe zadanie automatycznie po zainicjowaniu, gdy kod użytkownika tworzy wątek przy użyciu typów w <xref:System.Threading> przestrzeni nazw lub zwiększenie rozmiaru puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="5f4e7-128">Tworzy również zadania, gdy kod niezarządzany wykonuje wywołanie do funkcji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="5f4e7-129">`CreateTask`umożliwia hostowi jawne żądanie utworzenia nowego zadania przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="5f4e7-130">Na przykład host może wywołać tę metodę, aby wstępnie zainicjować struktury danych.</span><span class="sxs-lookup"><span data-stu-id="5f4e7-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5f4e7-131">Nowe zadanie jest zwracane w stanie wstrzymania i pozostaje zawieszone, dopóki Host jawnie wywoła [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="5f4e7-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f4e7-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f4e7-132">Requirements</span></span>  
 <span data-ttu-id="5f4e7-133">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f4e7-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f4e7-134">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5f4e7-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f4e7-135">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f4e7-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f4e7-136">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f4e7-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4e7-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f4e7-137">See also</span></span>

- [<span data-ttu-id="5f4e7-138">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f4e7-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="5f4e7-139">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f4e7-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="5f4e7-140">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f4e7-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="5f4e7-141">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f4e7-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
