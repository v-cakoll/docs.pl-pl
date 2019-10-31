---
title: IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 4400fab27ed82e540230ce4196844285e8e37d16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128636"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="51d88-102">IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="51d88-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="51d88-103">Rejestruje wskaźnik do funkcji wywołania zwrotnego, którą Host wywołuje, aby powiadomić środowisko uruchomieniowe języka wspólnego (CLR) o bieżącym obciążeniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="51d88-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d88-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51d88-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51d88-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51d88-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="51d88-106">podczas Wskaźnik interfejsu do wystąpienia [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) , który jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="51d88-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51d88-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="51d88-107">Return Value</span></span>  
  
|<span data-ttu-id="51d88-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51d88-108">HRESULT</span></span>|<span data-ttu-id="51d88-109">Opis</span><span class="sxs-lookup"><span data-stu-id="51d88-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51d88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="51d88-110">S_OK</span></span>|<span data-ttu-id="51d88-111">`RegisterMemoryNotificationCallback` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="51d88-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="51d88-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51d88-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51d88-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="51d88-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51d88-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51d88-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51d88-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="51d88-115">The call timed out.</span></span>|  
|<span data-ttu-id="51d88-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51d88-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51d88-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="51d88-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51d88-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51d88-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51d88-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="51d88-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51d88-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51d88-120">E_FAIL</span></span>|<span data-ttu-id="51d88-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="51d88-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51d88-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="51d88-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51d88-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="51d88-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51d88-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51d88-124">Remarks</span></span>  
 <span data-ttu-id="51d88-125">Ponieważ interfejs `ICLRMemoryNotificationCallback` definiuje tylko jedną metodę ([ICLRMemoryNotificationCallback:: OnMemoryNotification —](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), a ponieważ `pCallback` jest wskaźnikiem do wystąpienia `ICLRMemoryNotificationCallback` dostarczonego przez środowisko CLR, rejestracja jest efektywnie stosowana dla wywołania zwrotnego sama funkcja.</span><span class="sxs-lookup"><span data-stu-id="51d88-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="51d88-126">Host wywołuje `OnMemoryNotification`, aby zgłosić warunki ciśnienia pamięci zamiast używać standardowej funkcji `CreateMemoryResourceNotification` Win32.</span><span class="sxs-lookup"><span data-stu-id="51d88-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="51d88-127">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="51d88-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51d88-128">Wywołania do `OnMemoryNotification` nigdy nie blokują.</span><span class="sxs-lookup"><span data-stu-id="51d88-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="51d88-129">Zawsze są zwracane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="51d88-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51d88-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51d88-130">Requirements</span></span>  
 <span data-ttu-id="51d88-131">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51d88-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d88-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="51d88-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51d88-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51d88-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51d88-134">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d88-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d88-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51d88-135">See also</span></span>

- [<span data-ttu-id="51d88-136">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="51d88-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="51d88-137">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="51d88-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
