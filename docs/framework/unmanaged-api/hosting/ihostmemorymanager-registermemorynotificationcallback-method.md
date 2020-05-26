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
ms.openlocfilehash: 0c20df85560f715e829fe02be599788854fcb0f1
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804479"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="1f2a6-102">IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f2a6-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="1f2a6-103">Rejestruje wskaźnik do funkcji wywołania zwrotnego, którą Host wywołuje, aby powiadomić środowisko uruchomieniowe języka wspólnego (CLR) o bieżącym obciążeniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f2a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f2a6-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f2a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f2a6-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="1f2a6-106">podczas Wskaźnik interfejsu do wystąpienia [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) , który jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f2a6-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f2a6-107">Return Value</span></span>  
  
|<span data-ttu-id="1f2a6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f2a6-108">HRESULT</span></span>|<span data-ttu-id="1f2a6-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1f2a6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f2a6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f2a6-110">S_OK</span></span>|<span data-ttu-id="1f2a6-111">`RegisterMemoryNotificationCallback`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="1f2a6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f2a6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f2a6-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f2a6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f2a6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f2a6-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f2a6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f2a6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f2a6-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f2a6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f2a6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f2a6-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f2a6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f2a6-120">E_FAIL</span></span>|<span data-ttu-id="1f2a6-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f2a6-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f2a6-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f2a6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f2a6-124">Remarks</span></span>  
 <span data-ttu-id="1f2a6-125">Ponieważ `ICLRMemoryNotificationCallback` Interfejs definiuje tylko jedną metodę ([ICLRMemoryNotificationCallback:: OnMemoryNotification —](iclrmemorynotificationcallback-onmemorynotification-method.md)), a ponieważ `pCallback` jest wskaźnikiem do `ICLRMemoryNotificationCallback` wystąpienia dostarczonego przez środowisko CLR, rejestracja jest skuteczna dla samej funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="1f2a6-126">Host wywołuje `OnMemoryNotification` , aby zgłosić warunki ciśnienia pamięci zamiast używać standardowej `CreateMemoryResourceNotification` funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="1f2a6-127">Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f2a6-128">Wywołania `OnMemoryNotification` nigdy nie blokują.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="1f2a6-129">Zawsze są zwracane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="1f2a6-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f2a6-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f2a6-130">Requirements</span></span>  
 <span data-ttu-id="1f2a6-131">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f2a6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f2a6-132">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1f2a6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f2a6-133">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1f2a6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f2a6-134">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f2a6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2a6-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f2a6-135">See also</span></span>

- [<span data-ttu-id="1f2a6-136">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1f2a6-136">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="1f2a6-137">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f2a6-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
