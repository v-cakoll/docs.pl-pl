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
ms.openlocfilehash: f7426585045c7ae81377ec9bfca9d397d6f734cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192018"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="4e654-102">IHostSyncManager::CreateMonitorEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e654-102">IHostSyncManager::CreateMonitorEvent Method</span></span>
<span data-ttu-id="4e654-103">Tworzy monitorowany obiekt zdarzenia autoresetowania.</span><span class="sxs-lookup"><span data-stu-id="4e654-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e654-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e654-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e654-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e654-105">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="4e654-106">podczas Plik cookie do skojarzenia z obiektem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4e654-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4e654-107">określoną Wskaźnik do adresu wystąpienia [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) lub wartość null, jeśli nie można utworzyć obiektu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4e654-107">[out] A pointer to the address of an [IHostAutoEvent](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4e654-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4e654-108">Return Value</span></span>  
  
|<span data-ttu-id="4e654-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4e654-109">HRESULT</span></span>|<span data-ttu-id="4e654-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4e654-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4e654-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4e654-111">S_OK</span></span>|<span data-ttu-id="4e654-112">`CreateMonitorEvent` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="4e654-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4e654-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4e654-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4e654-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4e654-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4e654-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4e654-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4e654-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4e654-116">The call timed out.</span></span>|  
|<span data-ttu-id="4e654-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4e654-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4e654-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="4e654-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4e654-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4e654-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4e654-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="4e654-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4e654-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4e654-121">E_FAIL</span></span>|<span data-ttu-id="4e654-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="4e654-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4e654-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="4e654-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4e654-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4e654-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4e654-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4e654-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4e654-126">Za mało dostępnej pamięci, aby utworzyć żądany obiekt zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4e654-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e654-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e654-127">Remarks</span></span>  
 <span data-ttu-id="4e654-128">`CreateMonitorEvent` zwraca `IHostAutoEvent`, które są używane przez środowisko CLR w swojej implementacji typu zarządzanego <xref:System.Threading.Monitor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4e654-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="4e654-129">Ta metoda odzwierciedla funkcję `CreateEvent` Win32 z wartością `false` określoną dla parametru `bManualReset`.</span><span class="sxs-lookup"><span data-stu-id="4e654-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="4e654-130">Host może użyć pliku cookie, aby określić, które zadanie oczekuje na monitor, wywołując metodę [ICLRSyncManager:: GetMonitorOwner —](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4e654-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e654-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e654-131">Requirements</span></span>  
 <span data-ttu-id="4e654-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e654-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e654-133">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4e654-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e654-134">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4e654-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e654-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e654-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e654-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e654-136">See also</span></span>

- [<span data-ttu-id="4e654-137">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e654-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4e654-138">IHostAutoEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e654-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="4e654-139">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4e654-139">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
