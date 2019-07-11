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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 173eda2882ca9172c840d0d4fa65ef972fd779da
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749326"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="fc964-102">IHostTaskManager::SetUILocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc964-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="fc964-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) została zmieniona, ustawienia regionalne interfejsu użytkownika lub kultury na aktualnie przeprowadzane zadanie.</span><span class="sxs-lookup"><span data-stu-id="fc964-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc964-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc964-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc964-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc964-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="fc964-106">[in] Wartość identyfikatora ustawień regionalnych, który jest mapowany do nowo przypisanej geograficzne kultury i języka.</span><span class="sxs-lookup"><span data-stu-id="fc964-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc964-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc964-107">Return Value</span></span>  
  
|<span data-ttu-id="fc964-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc964-108">HRESULT</span></span>|<span data-ttu-id="fc964-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fc964-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc964-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc964-110">S_OK</span></span>|<span data-ttu-id="fc964-111">`SetUILocale` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fc964-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="fc964-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc964-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc964-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fc964-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc964-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc964-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc964-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fc964-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc964-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc964-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc964-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="fc964-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc964-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc964-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc964-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fc964-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc964-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc964-120">E_FAIL</span></span>|<span data-ttu-id="fc964-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fc964-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc964-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fc964-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc964-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc964-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fc964-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fc964-124">E_NOTIMPL</span></span>|<span data-ttu-id="fc964-125">Host nie zezwala na kod zarządzanego użytkownika, aby zmienić kulturę interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fc964-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc964-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc964-126">Remarks</span></span>  
 <span data-ttu-id="fc964-127">Środowisko uruchomieniowe wywołuje `SetUILocale` po wartości <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> właściwość zostanie zmieniony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="fc964-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="fc964-128">Ta metoda zapewnia możliwość hosta do wykonywania jakichkolwiek mechanizmów środowiska użytkownika, który może mieć do synchronizacji ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="fc964-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="fc964-129">Jeśli host nie zezwala na ustawienia regionalne interfejsu użytkownika można zmienić z poziomu kodu zarządzanego lub nie implementuje mechanizm do synchronizowania ustawień regionalnych, powinna zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="fc964-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc964-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc964-130">Requirements</span></span>  
 <span data-ttu-id="fc964-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc964-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc964-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc964-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc964-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc964-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc964-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc964-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc964-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc964-135">See also</span></span>

- [<span data-ttu-id="fc964-136">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc964-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="fc964-137">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc964-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="fc964-138">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc964-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="fc964-139">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc964-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="fc964-140">SetLocale, metoda</span><span class="sxs-lookup"><span data-stu-id="fc964-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
