---
title: IHostSyncManager::CreateManualEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 13679b4d40e660dfdd18e6fbafe19226b2ffda37
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195866"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="7d16f-102">IHostSyncManager::CreateManualEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d16f-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="7d16f-103">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="7d16f-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d16f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d16f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d16f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d16f-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="7d16f-106">[in] `true`, jeśli obiekt jest zasygnalizowani; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="7d16f-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="7d16f-107">określoną Wskaźnik do adresu wystąpienia [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) lub wartość null, jeśli nie można utworzyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d16f-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d16f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7d16f-108">Return Value</span></span>  
  
|<span data-ttu-id="7d16f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d16f-109">HRESULT</span></span>|<span data-ttu-id="7d16f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="7d16f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d16f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d16f-111">S_OK</span></span>|<span data-ttu-id="7d16f-112">`CreateManualEvent` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7d16f-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="7d16f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d16f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d16f-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7d16f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d16f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d16f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d16f-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="7d16f-116">The call timed out.</span></span>|  
|<span data-ttu-id="7d16f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d16f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d16f-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7d16f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d16f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d16f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d16f-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="7d16f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d16f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d16f-121">E_FAIL</span></span>|<span data-ttu-id="7d16f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7d16f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d16f-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="7d16f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d16f-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d16f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d16f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7d16f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7d16f-126">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7d16f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d16f-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d16f-127">Remarks</span></span>  
 <span data-ttu-id="7d16f-128">`CreateManualEvent` tworzy `IHostManualEvent`, obiekt zdarzenia resetowania ręcznego, który wymaga wywołania metody [IHostManualEvent:: Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) , aby ustawić ją w stanie niesygnalizującym.</span><span class="sxs-lookup"><span data-stu-id="7d16f-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="7d16f-129">`CreateManualEvent` odzwierciedla funkcję Win32 `CreateEvent` z wartością `true` określoną dla parametru `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="7d16f-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d16f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d16f-130">Requirements</span></span>  
 <span data-ttu-id="7d16f-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d16f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d16f-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7d16f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d16f-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7d16f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d16f-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d16f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d16f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d16f-135">See also</span></span>

- [<span data-ttu-id="7d16f-136">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d16f-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="7d16f-137">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d16f-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="7d16f-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d16f-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
