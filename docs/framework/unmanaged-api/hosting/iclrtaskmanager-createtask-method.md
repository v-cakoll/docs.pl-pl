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
ms.openlocfilehash: a801afeac690c02ef08652a923c31be14967cdc0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465794"
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="da722-102">ICLRTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="da722-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="da722-103">Żąda jawnie, że środowisko uruchomieniowe języka wspólnego (CLR) Utwórz nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="da722-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da722-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da722-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da722-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da722-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="da722-106">[out] Wskaźnik do adresu nowo utworzonego [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="da722-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da722-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="da722-107">Return Value</span></span>  
  
|<span data-ttu-id="da722-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da722-108">HRESULT</span></span>|<span data-ttu-id="da722-109">Opis</span><span class="sxs-lookup"><span data-stu-id="da722-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da722-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="da722-110">S_OK</span></span>|<span data-ttu-id="da722-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="da722-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="da722-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da722-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da722-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="da722-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="da722-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="da722-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="da722-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="da722-115">The call timed out.</span></span>|  
|<span data-ttu-id="da722-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="da722-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="da722-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="da722-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="da722-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="da722-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="da722-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="da722-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="da722-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da722-120">E_FAIL</span></span>|<span data-ttu-id="da722-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="da722-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="da722-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="da722-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="da722-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="da722-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="da722-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="da722-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="da722-125">Nie ma wystarczającej ilości pamięci jest dostępna do przydzielenia do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="da722-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da722-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da722-126">Remarks</span></span>  
 <span data-ttu-id="da722-127">Środowisko CLR tworzy nowe zadanie automatycznie po zainicjowaniu, gdy kod użytkownika tworzy wątek przy użyciu typów w <xref:System.Threading> przestrzeni nazw, lub po zwiększeniu rozmiaru puli wątków.</span><span class="sxs-lookup"><span data-stu-id="da722-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="da722-128">Tworzy również zadania, gdy kod niezarządzany sprawia, że wywołanie funkcji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="da722-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="da722-129">`CreateTask` Zezwalaj hostowi na jawnie zażądać, środowisko CLR, Utwórz nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="da722-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="da722-130">Na przykład host wywołać tę metodę w celu preinitialize struktur danych.</span><span class="sxs-lookup"><span data-stu-id="da722-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="da722-131">Nowe zadanie, zwracany jest w stanie wstrzymania i Kreator nie wznawia działania do momentu jawnego wywołania hosta [ihosttask::Start —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="da722-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da722-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da722-132">Requirements</span></span>  
 <span data-ttu-id="da722-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da722-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da722-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da722-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da722-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da722-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da722-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da722-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da722-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da722-137">See also</span></span>
- [<span data-ttu-id="da722-138">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="da722-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="da722-139">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da722-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="da722-140">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="da722-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="da722-141">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="da722-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
