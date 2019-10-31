---
title: ICLRTaskManager::SetUILocale — Metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: 051bd5cb846eb4e6e3390e17b3011a1c5b50bc45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127875"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="aa9fe-102">ICLRTaskManager::SetUILocale — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa9fe-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="aa9fe-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o zmodyfikowaniu przez hosta ustawień regionalnych (UI) interfejsu użytkownika lub kulturze w aktualnie wykonywanym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa9fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa9fe-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa9fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa9fe-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="aa9fe-106">podczas Wartość identyfikatora ustawień regionalnych, która jest mapowana na nowo przypisaną kulturę geograficzną i język interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa9fe-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa9fe-107">Return Value</span></span>  
  
|<span data-ttu-id="aa9fe-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa9fe-108">HRESULT</span></span>|<span data-ttu-id="aa9fe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="aa9fe-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa9fe-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa9fe-110">S_OK</span></span>|<span data-ttu-id="aa9fe-111">`SetUILocale` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="aa9fe-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa9fe-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa9fe-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa9fe-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa9fe-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa9fe-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-115">The call timed out.</span></span>|  
|<span data-ttu-id="aa9fe-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa9fe-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa9fe-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa9fe-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa9fe-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa9fe-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa9fe-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa9fe-120">E_FAIL</span></span>|<span data-ttu-id="aa9fe-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa9fe-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa9fe-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa9fe-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa9fe-124">Remarks</span></span>  
 <span data-ttu-id="aa9fe-125">`SetUILocale` umożliwia hostowi wykonywanie wszelkich mechanizmów, które mogą być związane z synchronizacją ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="aa9fe-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9fe-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa9fe-126">Requirements</span></span>  
 <span data-ttu-id="aa9fe-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa9fe-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9fe-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa9fe-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa9fe-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aa9fe-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa9fe-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9fe-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa9fe-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa9fe-131">See also</span></span>

- [<span data-ttu-id="aa9fe-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa9fe-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="aa9fe-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa9fe-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="aa9fe-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa9fe-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="aa9fe-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa9fe-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
