---
title: IHostTaskManager::SetLocale — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79d4c5b2b2bbe821ff546324fd3af04cb3472e4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149828"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f0a29-102">IHostTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0a29-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f0a29-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) została zmieniona, ustawienia regionalne lub kultury na aktualnie przeprowadzane zadanie.</span><span class="sxs-lookup"><span data-stu-id="f0a29-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0a29-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0a29-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0a29-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f0a29-106">[in] Wartość identyfikatora ustawień regionalnych, który jest mapowany do nowo przypisanej geograficzne kultury i języka.</span><span class="sxs-lookup"><span data-stu-id="f0a29-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0a29-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0a29-107">Return Value</span></span>  
  
|<span data-ttu-id="f0a29-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0a29-108">HRESULT</span></span>|<span data-ttu-id="f0a29-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f0a29-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0a29-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0a29-110">S_OK</span></span>|`SetLocale` <span data-ttu-id="f0a29-111">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f0a29-111">returned successfully.</span></span>|  
|<span data-ttu-id="f0a29-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f0a29-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f0a29-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0a29-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f0a29-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f0a29-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f0a29-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0a29-115">The call timed out.</span></span>|  
|<span data-ttu-id="f0a29-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f0a29-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f0a29-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="f0a29-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f0a29-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f0a29-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f0a29-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f0a29-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f0a29-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f0a29-120">E_FAIL</span></span>|<span data-ttu-id="f0a29-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f0a29-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f0a29-122">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f0a29-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f0a29-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f0a29-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f0a29-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f0a29-124">E_NOTIMPL</span></span>|<span data-ttu-id="f0a29-125">Host nie zezwala na kodu zarządzanego użytkownika do modyfikowania ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="f0a29-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0a29-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0a29-126">Remarks</span></span>  
 <span data-ttu-id="f0a29-127">Środowisko uruchomieniowe wywołuje `SetLocale` po wartości <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwość zostanie zmieniony przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="f0a29-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f0a29-128">Ta metoda zapewnia możliwość hosta do wykonywania jakichkolwiek mechanizmów środowiska użytkownika, który może mieć do synchronizacji ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="f0a29-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f0a29-129">Jeśli host nie zezwala na ustawienia regionalne, które można zmienić z poziomu kodu zarządzanego lub nie implementuje mechanizm do synchronizowania ustawień regionalnych, powinna zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="f0a29-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0a29-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0a29-130">Requirements</span></span>  
 <span data-ttu-id="f0a29-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0a29-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0a29-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0a29-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0a29-133">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0a29-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f0a29-134">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f0a29-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0a29-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0a29-135">See also</span></span>

- [<span data-ttu-id="f0a29-136">ICLRTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0a29-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f0a29-137">ICLRTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0a29-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f0a29-138">IHostTask — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0a29-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f0a29-139">IHostTaskManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f0a29-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f0a29-140">SetUILocale, metoda</span><span class="sxs-lookup"><span data-stu-id="f0a29-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
