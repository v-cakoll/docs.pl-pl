---
title: ICLRTaskManager::SetLocale — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 79f24b3ccacd84037042a883d3a034bb7b4d200a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092088"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="daba9-102">ICLRTaskManager::SetLocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="daba9-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="daba9-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR), że host zmodyfikował wartość identyfikatora ustawień regionalnych (która jest mapowana na kulturę geograficzną i język) w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="daba9-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daba9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="daba9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daba9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="daba9-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="daba9-106">podczas Wartość identyfikatora ustawień regionalnych, która jest mapowana na nowo przypisaną kulturę geograficzną i język.</span><span class="sxs-lookup"><span data-stu-id="daba9-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daba9-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="daba9-107">Return Value</span></span>  
  
|<span data-ttu-id="daba9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="daba9-108">HRESULT</span></span>|<span data-ttu-id="daba9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="daba9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="daba9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="daba9-110">S_OK</span></span>|<span data-ttu-id="daba9-111">Metoda została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="daba9-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="daba9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="daba9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="daba9-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="daba9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="daba9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="daba9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="daba9-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="daba9-115">The call timed out.</span></span>|  
|<span data-ttu-id="daba9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="daba9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="daba9-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="daba9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="daba9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="daba9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="daba9-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="daba9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="daba9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="daba9-120">E_FAIL</span></span>|<span data-ttu-id="daba9-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="daba9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="daba9-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="daba9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="daba9-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="daba9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daba9-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="daba9-124">Remarks</span></span>  
 <span data-ttu-id="daba9-125">`SetLocale` zapewnia hostowi możliwość wykonywania wszelkich mechanizmów, które mogą być związane z synchronizacją ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="daba9-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daba9-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="daba9-126">Requirements</span></span>  
 <span data-ttu-id="daba9-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daba9-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daba9-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="daba9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="daba9-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="daba9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daba9-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daba9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daba9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="daba9-131">See also</span></span>

- [<span data-ttu-id="daba9-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="daba9-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="daba9-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="daba9-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="daba9-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="daba9-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="daba9-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="daba9-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
