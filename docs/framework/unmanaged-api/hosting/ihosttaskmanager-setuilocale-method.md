---
title: IHostTaskManager::SetUILocale — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132941"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="a949c-102">IHostTaskManager::SetUILocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="a949c-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="a949c-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) zmieniło ustawienia regionalne interfejsu użytkownika (UI) lub kulturę, w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="a949c-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a949c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a949c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a949c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a949c-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="a949c-106">podczas Wartość identyfikatora ustawień regionalnych, która jest mapowana na nowo przypisaną kulturę geograficzną i język.</span><span class="sxs-lookup"><span data-stu-id="a949c-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a949c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a949c-107">Return Value</span></span>  
  
|<span data-ttu-id="a949c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a949c-108">HRESULT</span></span>|<span data-ttu-id="a949c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a949c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a949c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a949c-110">S_OK</span></span>|<span data-ttu-id="a949c-111">`SetUILocale` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a949c-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="a949c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a949c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a949c-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a949c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a949c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a949c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a949c-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a949c-115">The call timed out.</span></span>|  
|<span data-ttu-id="a949c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a949c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a949c-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a949c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a949c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a949c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a949c-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a949c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a949c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a949c-120">E_FAIL</span></span>|<span data-ttu-id="a949c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a949c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a949c-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a949c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a949c-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a949c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a949c-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a949c-124">E_NOTIMPL</span></span>|<span data-ttu-id="a949c-125">Host nie zezwala na zmianę kultury interfejsu użytkownika przez zarządzany kod.</span><span class="sxs-lookup"><span data-stu-id="a949c-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a949c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a949c-126">Remarks</span></span>  
 <span data-ttu-id="a949c-127">Wywołania środowiska uruchomieniowego `SetUILocale`, gdy wartość właściwości <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> jest zmieniana przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="a949c-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="a949c-128">Ta metoda zapewnia dla hosta możliwość wykonywania wszelkich mechanizmów, które mogą mieć na celu synchronizację ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="a949c-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="a949c-129">Jeśli host nie zezwala na zmianę ustawień regionalnych interfejsu użytkownika z kodu zarządzanego lub nie implementuje mechanizmu synchronizacji ustawień lokalnych, powinien zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="a949c-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a949c-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a949c-130">Requirements</span></span>  
 <span data-ttu-id="a949c-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a949c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a949c-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a949c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a949c-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a949c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a949c-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a949c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a949c-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a949c-135">See also</span></span>

- [<span data-ttu-id="a949c-136">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a949c-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a949c-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a949c-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a949c-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="a949c-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a949c-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a949c-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="a949c-140">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="a949c-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
