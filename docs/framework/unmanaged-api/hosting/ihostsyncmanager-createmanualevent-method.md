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
ms.openlocfilehash: ecf53606dd12b517d9ec31ab25f98452d35bdf98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="8ca16-102">IHostSyncManager::CreateManualEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="8ca16-102">IHostSyncManager::CreateManualEvent Method</span></span>
<span data-ttu-id="8ca16-103">Tworzy obiekt zdarzenia resetowania ręcznego.</span><span class="sxs-lookup"><span data-stu-id="8ca16-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ca16-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ca16-104">Syntax</span></span>  
  
```  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ca16-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8ca16-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="8ca16-106">[in] `true`, jeśli obiekt jest sygnałowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8ca16-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8ca16-107">[out] Wskaźnik do adresu [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ca16-107">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ca16-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8ca16-108">Return Value</span></span>  
  
|<span data-ttu-id="8ca16-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8ca16-109">HRESULT</span></span>|<span data-ttu-id="8ca16-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8ca16-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ca16-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8ca16-111">S_OK</span></span>|<span data-ttu-id="8ca16-112">`CreateManualEvent` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8ca16-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8ca16-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8ca16-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8ca16-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8ca16-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8ca16-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8ca16-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8ca16-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8ca16-116">The call timed out.</span></span>|  
|<span data-ttu-id="8ca16-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8ca16-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8ca16-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8ca16-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8ca16-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8ca16-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8ca16-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8ca16-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8ca16-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8ca16-121">E_FAIL</span></span>|<span data-ttu-id="8ca16-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8ca16-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8ca16-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8ca16-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8ca16-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8ca16-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8ca16-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8ca16-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8ca16-126">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ca16-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ca16-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ca16-127">Remarks</span></span>  
 <span data-ttu-id="8ca16-128">`CreateManualEvent` Tworzy `IHostManualEvent`, obiekt zdarzeniach, resetowanego ręcznie, który wymaga wywołania [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) metody, aby ustawić stan sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="8ca16-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="8ca16-129">`CreateManualEvent` odzwierciedla Win32 `CreateEvent` funkcja o wartości `true` określona dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="8ca16-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ca16-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ca16-130">Requirements</span></span>  
 <span data-ttu-id="8ca16-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca16-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ca16-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8ca16-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8ca16-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ca16-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ca16-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ca16-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca16-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ca16-135">See Also</span></span>  
 [<span data-ttu-id="8ca16-136">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ca16-136">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8ca16-137">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ca16-137">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="8ca16-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8ca16-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
