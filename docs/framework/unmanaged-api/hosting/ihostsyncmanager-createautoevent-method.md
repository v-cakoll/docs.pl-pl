---
title: IHostSyncManager::CreateAutoEvent — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe1b685f50f793f7451187f17adc848ec9d4422f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440206"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a><span data-ttu-id="a3fce-102">IHostSyncManager::CreateAutoEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3fce-102">IHostSyncManager::CreateAutoEvent Method</span></span>
<span data-ttu-id="a3fce-103">Tworzy obiekt zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="a3fce-103">Creates an auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3fce-104">Syntax</span></span>  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3fce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3fce-105">Parameters</span></span>  
 `ppEvent`  
 <span data-ttu-id="a3fce-106">[out] Wskaźnik do adresu [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienie implementowane przez hosta lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3fce-106">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance implemented by the host, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3fce-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3fce-107">Return Value</span></span>  
  
|<span data-ttu-id="a3fce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3fce-108">HRESULT</span></span>|<span data-ttu-id="a3fce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a3fce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3fce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3fce-110">S_OK</span></span>|<span data-ttu-id="a3fce-111">`CreateAutoEvent` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a3fce-111">`CreateAutoEvent` returned successfully.</span></span>|  
|<span data-ttu-id="a3fce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3fce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3fce-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a3fce-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3fce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3fce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3fce-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a3fce-115">The call timed out.</span></span>|  
|<span data-ttu-id="a3fce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3fce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3fce-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a3fce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3fce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3fce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3fce-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a3fce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3fce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3fce-120">E_FAIL</span></span>|<span data-ttu-id="a3fce-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a3fce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3fce-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a3fce-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3fce-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a3fce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3fce-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a3fce-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="a3fce-125">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a3fce-125">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3fce-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3fce-126">Remarks</span></span>  
 <span data-ttu-id="a3fce-127">`CreateAutoEvent` Tworzy obiekt automatycznie — zdarzenie, którego stan jest automatycznie zmieniany na innych niż sygnalizowane po oczekiwania wątku został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="a3fce-127">`CreateAutoEvent` creates an auto-event object whose state is automatically changed to non-signaled after the waiting thread has been released.</span></span> <span data-ttu-id="a3fce-128">Ta metoda odzwierciedla Win32 `CreateEvent` funkcja o wartości `false` określona dla `bManualReset` parametru</span><span class="sxs-lookup"><span data-stu-id="a3fce-128">This method mirrors the Win32 `CreateEvent` function with a value of `false` specified for the `bManualReset` parameter</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3fce-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3fce-129">Requirements</span></span>  
 <span data-ttu-id="a3fce-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fce-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fce-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3fce-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3fce-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3fce-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3fce-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3fce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fce-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3fce-134">See Also</span></span>  
 [<span data-ttu-id="a3fce-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fce-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="a3fce-136">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fce-136">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="a3fce-137">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fce-137">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="a3fce-138">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fce-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
