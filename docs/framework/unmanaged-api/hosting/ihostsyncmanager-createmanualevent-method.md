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
ms.openlocfilehash: ada9a3131ea3063239ab7897d0096f0accbd0f94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137738"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="6856f-102">IHostSyncManager::CreateManualEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="6856f-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="6856f-103">Tworzy obiekt zdarzenie resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="6856f-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6856f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6856f-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6856f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6856f-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="6856f-106">[in] `true`, jeśli obiekt jest sygnałowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="6856f-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="6856f-107">[out] Wskaźnik na adres [ihostmanualevent —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6856f-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6856f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6856f-108">Return Value</span></span>  
  
|<span data-ttu-id="6856f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6856f-109">HRESULT</span></span>|<span data-ttu-id="6856f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6856f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6856f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6856f-111">S_OK</span></span>|`CreateManualEvent` <span data-ttu-id="6856f-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="6856f-112">returned successfully.</span></span>|  
|<span data-ttu-id="6856f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6856f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6856f-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6856f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6856f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6856f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6856f-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="6856f-116">The call timed out.</span></span>|  
|<span data-ttu-id="6856f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6856f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6856f-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="6856f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6856f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6856f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6856f-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="6856f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6856f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6856f-121">E_FAIL</span></span>|<span data-ttu-id="6856f-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6856f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6856f-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="6856f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6856f-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6856f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6856f-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="6856f-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="6856f-126">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6856f-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6856f-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6856f-127">Remarks</span></span>  
 `CreateManualEvent` <span data-ttu-id="6856f-128">Tworzy `IHostManualEvent`, obiekt zdarzeniach, resetowanego ręcznie, który wymaga wywołania [ihostmanualevent::reset —](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) metodę, aby ustawić go do stanu zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="6856f-128">creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> `CreateManualEvent` <span data-ttu-id="6856f-129">odzwierciedla Win32 `CreateEvent` funkcji z wartością `true` określony dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="6856f-129">mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6856f-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6856f-130">Requirements</span></span>  
 <span data-ttu-id="6856f-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6856f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6856f-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6856f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6856f-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6856f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6856f-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6856f-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6856f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6856f-135">See also</span></span>

- [<span data-ttu-id="6856f-136">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6856f-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6856f-137">IHostManualEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6856f-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="6856f-138">IHostSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6856f-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
