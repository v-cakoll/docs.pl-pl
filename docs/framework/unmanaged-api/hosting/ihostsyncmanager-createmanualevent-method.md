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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8e12c6bd67ea5d22bb891057cae37e3c41ca233
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716859"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="6c837-102">IHostSyncManager::CreateManualEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c837-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="6c837-103">Tworzy obiekt zdarzenie resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="6c837-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c837-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c837-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c837-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c837-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="6c837-106">[in] `true`, jeśli obiekt jest sygnałowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6c837-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="6c837-107">[out] Wskaźnik na adres [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c837-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c837-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c837-108">Return Value</span></span>  
  
|<span data-ttu-id="6c837-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c837-109">HRESULT</span></span>|<span data-ttu-id="6c837-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6c837-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c837-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c837-111">S_OK</span></span>|<span data-ttu-id="6c837-112">`CreateManualEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6c837-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="6c837-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c837-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c837-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6c837-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c837-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c837-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c837-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6c837-116">The call timed out.</span></span>|  
|<span data-ttu-id="6c837-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c837-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c837-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6c837-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c837-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c837-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c837-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6c837-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c837-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c837-121">E_FAIL</span></span>|<span data-ttu-id="6c837-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6c837-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c837-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6c837-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c837-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c837-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c837-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6c837-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6c837-126">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6c837-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c837-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c837-127">Remarks</span></span>  
 <span data-ttu-id="6c837-128">`CreateManualEvent` Tworzy `IHostManualEvent`, obiekt zdarzeniach, resetowanego ręcznie, który wymaga wywołania [ihostmanualevent::reset —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) metodę, aby ustawić go do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="6c837-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="6c837-129">`CreateManualEvent` odzwierciedla Win32 `CreateEvent` funkcji z wartością `true` określony dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="6c837-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c837-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c837-130">Requirements</span></span>  
 <span data-ttu-id="6c837-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c837-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c837-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c837-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c837-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c837-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c837-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c837-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c837-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c837-135">See also</span></span>
- [<span data-ttu-id="6c837-136">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c837-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6c837-137">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c837-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="6c837-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c837-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
