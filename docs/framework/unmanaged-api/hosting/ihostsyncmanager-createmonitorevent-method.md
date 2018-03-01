---
title: "IHostSyncManager::CreateMonitorEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae12db71f4eae0f7d887fda26e05401f4f23ee5c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="353f2-102">IHostSyncManager::CreateMonitorEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="353f2-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="353f2-103">Tworzy obiekt monitorowanych zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="353f2-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="353f2-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="353f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="353f2-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="353f2-106">[in] Plik cookie do skojarzenia z obiektem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="353f2-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="353f2-107">[out] Wskaźnik do adresu [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia, lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="353f2-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353f2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="353f2-108">Return Value</span></span>  
  
|<span data-ttu-id="353f2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="353f2-109">HRESULT</span></span>|<span data-ttu-id="353f2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="353f2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="353f2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="353f2-111">S_OK</span></span>|<span data-ttu-id="353f2-112">`CreateMonitorEvent`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="353f2-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="353f2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="353f2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="353f2-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="353f2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="353f2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="353f2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="353f2-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="353f2-116">The call timed out.</span></span>|  
|<span data-ttu-id="353f2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="353f2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="353f2-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="353f2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="353f2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="353f2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="353f2-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="353f2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="353f2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="353f2-121">E_FAIL</span></span>|<span data-ttu-id="353f2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="353f2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="353f2-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="353f2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="353f2-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="353f2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="353f2-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="353f2-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="353f2-126">Za mało pamięci nie była dostępna do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="353f2-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="353f2-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="353f2-127">Remarks</span></span>  
 <span data-ttu-id="353f2-128">`CreateMonitorEvent`Zwraca `IHostAutoEvent` używającej CLR w jej implementacja zarządzanej <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="353f2-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="353f2-129">Ta metoda odzwierciedla Win32 `CreateEvent` funkcja o wartości `false` określona dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="353f2-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="353f2-130">Hosta może używać pliku cookie do określenia, które zadanie oczekuje na monitorze przez wywołanie metody [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="353f2-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353f2-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="353f2-131">Requirements</span></span>  
 <span data-ttu-id="353f2-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353f2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353f2-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="353f2-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="353f2-134">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="353f2-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="353f2-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353f2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353f2-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="353f2-136">See Also</span></span>  
 [<span data-ttu-id="353f2-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="353f2-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="353f2-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="353f2-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="353f2-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="353f2-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="353f2-140">Monitory</span><span class="sxs-lookup"><span data-stu-id="353f2-140">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)
