---
title: IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: b84e92ca356ad83421d788a732926b614ffa4a8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133789"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="66c20-102">IHostIoCompletionManager::SetCLRIoCompletionManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="66c20-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="66c20-103">Dostarcza host ze wskaźnikiem interfejsu do wystąpienia [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) zaimplementowanego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="66c20-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66c20-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66c20-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="66c20-106">podczas Wskaźnik interfejsu do wystąpienia `ICLRIoCompletionManager` dostarczonego przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="66c20-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66c20-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66c20-107">Return Value</span></span>  
  
|<span data-ttu-id="66c20-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66c20-108">HRESULT</span></span>|<span data-ttu-id="66c20-109">Opis</span><span class="sxs-lookup"><span data-stu-id="66c20-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66c20-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="66c20-110">S_OK</span></span>|<span data-ttu-id="66c20-111">`SetCLRIoCompletionManager` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="66c20-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="66c20-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66c20-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66c20-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="66c20-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66c20-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66c20-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66c20-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="66c20-115">The call timed out.</span></span>|  
|<span data-ttu-id="66c20-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66c20-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66c20-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="66c20-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66c20-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66c20-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66c20-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="66c20-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66c20-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66c20-120">E_FAIL</span></span>|<span data-ttu-id="66c20-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="66c20-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66c20-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="66c20-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66c20-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66c20-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66c20-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66c20-124">Remarks</span></span>  
 <span data-ttu-id="66c20-125">Po wywołaniu środowiska CLR `SetCLRIoCompletionManager`, host musi wywołać [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) w celu powiadomienia środowiska CLR o ukończeniu żądania we/wy.</span><span class="sxs-lookup"><span data-stu-id="66c20-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c20-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66c20-126">Requirements</span></span>  
 <span data-ttu-id="66c20-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c20-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c20-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66c20-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66c20-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66c20-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66c20-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c20-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c20-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66c20-131">See also</span></span>

- [<span data-ttu-id="66c20-132">ICLRIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="66c20-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="66c20-133">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="66c20-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
