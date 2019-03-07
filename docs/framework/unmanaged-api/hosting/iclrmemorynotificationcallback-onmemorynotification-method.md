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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d395c7eed27893e407b1944523a2f879b56c795d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489309"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="69284-102">ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="69284-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="69284-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="69284-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69284-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69284-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69284-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69284-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="69284-106">[in] Jedną z [ememoryavailable —](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) wartości, wskazując dużego wykorzystania pamięci komputera wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="69284-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69284-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69284-107">Return Value</span></span>  
  
|<span data-ttu-id="69284-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69284-108">HRESULT</span></span>|<span data-ttu-id="69284-109">Opis</span><span class="sxs-lookup"><span data-stu-id="69284-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69284-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="69284-110">S_OK</span></span>|<span data-ttu-id="69284-111">`OnMemoryNotification` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="69284-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="69284-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69284-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69284-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="69284-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69284-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="69284-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="69284-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="69284-115">The call timed out.</span></span>|  
|<span data-ttu-id="69284-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="69284-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="69284-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="69284-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="69284-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="69284-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="69284-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="69284-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="69284-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69284-120">E_FAIL</span></span>|<span data-ttu-id="69284-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="69284-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69284-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="69284-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69284-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="69284-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69284-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69284-124">Remarks</span></span>  
 <span data-ttu-id="69284-125">Środowisko CLR rejestruje wywołanie zwrotne w celu `OnMemoryNotification` za pomocą wywołania [ihostmemorymanager::registermemorynotificationcallback —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="69284-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="69284-126">Środowisko wykonawcze używa tych informacji, zwrócony podczas wywołania zwrotnego, aby zwolnić dodatkową pamięć, gdy host zgłosi tego zasoby są bardzo mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="69284-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69284-127">Wywołania `OnMemoryNotification` nigdy nie blokuj.</span><span class="sxs-lookup"><span data-stu-id="69284-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="69284-128">Zawsze zwracają natychmiast.</span><span class="sxs-lookup"><span data-stu-id="69284-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69284-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69284-129">Requirements</span></span>  
 <span data-ttu-id="69284-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69284-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69284-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69284-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69284-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="69284-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69284-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69284-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69284-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69284-134">See also</span></span>
- [<span data-ttu-id="69284-135">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="69284-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="69284-136">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="69284-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="69284-137">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="69284-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
