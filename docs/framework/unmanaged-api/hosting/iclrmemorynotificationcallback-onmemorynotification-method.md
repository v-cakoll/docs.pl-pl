---
title: ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: 11b9b500e16917498856888c437c58c0df2edafb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140990"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="fc73f-102">ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc73f-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="fc73f-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o załadowaniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fc73f-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc73f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc73f-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc73f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc73f-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="fc73f-106">podczas Jedna z wartości [EMemoryAvailable —](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) , wskazująca na to, że komputer jest aktualnie obecny.</span><span class="sxs-lookup"><span data-stu-id="fc73f-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc73f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc73f-107">Return Value</span></span>  
  
|<span data-ttu-id="fc73f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc73f-108">HRESULT</span></span>|<span data-ttu-id="fc73f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fc73f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc73f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc73f-110">S_OK</span></span>|<span data-ttu-id="fc73f-111">`OnMemoryNotification` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="fc73f-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="fc73f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc73f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc73f-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fc73f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc73f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc73f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc73f-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="fc73f-115">The call timed out.</span></span>|  
|<span data-ttu-id="fc73f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc73f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc73f-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fc73f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc73f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc73f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc73f-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="fc73f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc73f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc73f-120">E_FAIL</span></span>|<span data-ttu-id="fc73f-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fc73f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc73f-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="fc73f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc73f-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc73f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc73f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc73f-124">Remarks</span></span>  
 <span data-ttu-id="fc73f-125">Środowisko CLR rejestruje wywołanie zwrotne do `OnMemoryNotification` za pomocą wywołania metody [IHostMemoryManager:: RegisterMemoryNotificationCallback —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fc73f-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="fc73f-126">Środowisko uruchomieniowe używa informacji zwracanych w wywołaniu zwrotnym, aby zwolnić dodatkową pamięć, gdy host zgłasza, że zasoby pamięci są niskie.</span><span class="sxs-lookup"><span data-stu-id="fc73f-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc73f-127">Wywołania do `OnMemoryNotification` nigdy nie blokują.</span><span class="sxs-lookup"><span data-stu-id="fc73f-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="fc73f-128">Zawsze są zwracane natychmiast.</span><span class="sxs-lookup"><span data-stu-id="fc73f-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc73f-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc73f-129">Requirements</span></span>  
 <span data-ttu-id="fc73f-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc73f-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc73f-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc73f-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc73f-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc73f-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc73f-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc73f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc73f-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc73f-134">See also</span></span>

- [<span data-ttu-id="fc73f-135">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc73f-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="fc73f-136">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="fc73f-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="fc73f-137">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc73f-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
