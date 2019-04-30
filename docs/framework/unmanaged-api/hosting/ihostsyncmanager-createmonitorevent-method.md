---
title: IHostSyncManager::CreateMonitorEvent — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12b0e32ab46b3e8ba5120da4b16a10db85f105a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696304"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="86597-102">IHostSyncManager::CreateMonitorEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="86597-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="86597-103">Tworzy obiekt monitorowanych zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="86597-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86597-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86597-104">Syntax</span></span>  
  
```  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86597-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86597-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="86597-106">[in] Plik cookie do skojarzenia z obiektem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="86597-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="86597-107">[out] Wskaźnik na adres [ihostautoevent —](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) wystąpienia lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="86597-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86597-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="86597-108">Return Value</span></span>  
  
|<span data-ttu-id="86597-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="86597-109">HRESULT</span></span>|<span data-ttu-id="86597-110">Opis</span><span class="sxs-lookup"><span data-stu-id="86597-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="86597-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="86597-111">S_OK</span></span>|<span data-ttu-id="86597-112">`CreateMonitorEvent` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="86597-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="86597-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="86597-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="86597-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="86597-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="86597-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="86597-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="86597-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="86597-116">The call timed out.</span></span>|  
|<span data-ttu-id="86597-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="86597-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="86597-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="86597-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="86597-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="86597-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="86597-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="86597-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="86597-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="86597-121">E_FAIL</span></span>|<span data-ttu-id="86597-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="86597-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="86597-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="86597-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="86597-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="86597-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="86597-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="86597-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="86597-126">Za mało dostępnej pamięci na do utworzenia obiektu żądanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="86597-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86597-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86597-127">Remarks</span></span>  
 <span data-ttu-id="86597-128">`CreateMonitorEvent` Zwraca `IHostAutoEvent` , gdy środowisko CLR jest używany w jego implementacja obiektu zarządzanego <xref:System.Threading.Monitor?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="86597-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="86597-129">Ta metoda odzwierciedla Win32 `CreateEvent` funkcji z wartością `false` określony dla `bManualReset` parametru.</span><span class="sxs-lookup"><span data-stu-id="86597-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="86597-130">Hosta można użyć pliku cookie, aby określić, które zadanie oczekuje na monitorze, wywołując [iclrsyncmanager::getmonitorowner —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="86597-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86597-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86597-131">Requirements</span></span>  
 <span data-ttu-id="86597-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86597-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86597-133">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86597-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86597-134">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86597-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86597-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86597-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86597-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86597-136">See also</span></span>

- [<span data-ttu-id="86597-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="86597-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="86597-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="86597-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="86597-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="86597-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
