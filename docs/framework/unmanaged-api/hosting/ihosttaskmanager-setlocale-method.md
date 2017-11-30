---
title: "IHostTaskManager::SetLocale — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 885dd41a3bc5afb156d1f338fb3564731d5a742a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="0b4c8-102">IHostTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b4c8-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="0b4c8-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) została zmieniona, ustawienia regionalne lub kultury na aktualnie wykonywanego zadania.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b4c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b4c8-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b4c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b4c8-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0b4c8-106">[in] Wartość identyfikatora ustawień regionalnych mapy do nowo przypisanej kultury geograficzne i języka.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b4c8-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0b4c8-107">Return Value</span></span>  
  
|<span data-ttu-id="0b4c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b4c8-108">HRESULT</span></span>|<span data-ttu-id="0b4c8-109">Opis</span><span class="sxs-lookup"><span data-stu-id="0b4c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b4c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b4c8-110">S_OK</span></span>|<span data-ttu-id="0b4c8-111">`SetLocale`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="0b4c8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b4c8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b4c8-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b4c8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b4c8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b4c8-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b4c8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b4c8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b4c8-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b4c8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b4c8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b4c8-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b4c8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b4c8-120">E_FAIL</span></span>|<span data-ttu-id="0b4c8-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b4c8-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b4c8-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b4c8-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0b4c8-124">E_NOTIMPL</span></span>|<span data-ttu-id="0b4c8-125">Host nie zezwala na kod zarządzany użytkownika można zmodyfikować ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b4c8-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b4c8-126">Remarks</span></span>  
 <span data-ttu-id="0b4c8-127">Wywołania środowiska uruchomieniowego `SetLocale` podczas wartość <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> właściwości zostanie zmieniona przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="0b4c8-128">Ta metoda zapewnia możliwość hosta do wykonywania jakichkolwiek mechanizmów, który może mieć synchronizacji ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="0b4c8-129">Jeśli na hoście nie zezwala na ustawienia regionalne, które można zmienić z kodu zarządzanego lub nie implementuje mechanizm synchronizacji ustawień regionalnych, powinien on zwrócić E_NOTIMPL z tej metody.</span><span class="sxs-lookup"><span data-stu-id="0b4c8-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b4c8-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b4c8-130">Requirements</span></span>  
 <span data-ttu-id="0b4c8-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b4c8-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b4c8-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b4c8-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b4c8-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b4c8-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b4c8-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b4c8-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b4c8-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b4c8-135">See Also</span></span>  
 [<span data-ttu-id="0b4c8-136">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b4c8-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="0b4c8-137">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b4c8-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="0b4c8-138">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b4c8-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="0b4c8-139">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="0b4c8-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="0b4c8-140">SetUILocale — metoda</span><span class="sxs-lookup"><span data-stu-id="0b4c8-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
