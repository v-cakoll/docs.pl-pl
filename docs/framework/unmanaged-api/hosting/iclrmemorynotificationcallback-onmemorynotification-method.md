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
ms.openlocfilehash: c318b6f395e8bd7ccddf5fcbfc4acfcb11087fdf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722559"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="a1808-102">ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1808-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="a1808-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a1808-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1808-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1808-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1808-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1808-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="a1808-106">[in] Jedną z [ememoryavailable —](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) wartości, wskazując dużego wykorzystania pamięci komputera wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="a1808-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1808-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1808-107">Return Value</span></span>  
  
|<span data-ttu-id="a1808-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1808-108">HRESULT</span></span>|<span data-ttu-id="a1808-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a1808-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1808-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1808-110">S_OK</span></span>|<span data-ttu-id="a1808-111">`OnMemoryNotification` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a1808-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="a1808-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1808-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1808-113">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1808-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1808-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1808-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1808-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a1808-115">The call timed out.</span></span>|  
|<span data-ttu-id="a1808-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1808-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1808-117">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a1808-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1808-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1808-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1808-119">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a1808-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1808-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1808-120">E_FAIL</span></span>|<span data-ttu-id="a1808-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a1808-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1808-122">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a1808-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1808-123">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a1808-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1808-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1808-124">Remarks</span></span>  
 <span data-ttu-id="a1808-125">Środowisko CLR rejestruje wywołanie zwrotne w celu `OnMemoryNotification` za pomocą wywołania [ihostmemorymanager::registermemorynotificationcallback —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a1808-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="a1808-126">Środowisko wykonawcze używa tych informacji, zwrócony podczas wywołania zwrotnego, aby zwolnić dodatkową pamięć, gdy host zgłosi tego zasoby są bardzo mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="a1808-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1808-127">Wywołania `OnMemoryNotification` nigdy nie blokuj.</span><span class="sxs-lookup"><span data-stu-id="a1808-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="a1808-128">Zawsze zwracają natychmiast.</span><span class="sxs-lookup"><span data-stu-id="a1808-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1808-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1808-129">Requirements</span></span>  
 <span data-ttu-id="a1808-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1808-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1808-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1808-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1808-132">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1808-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1808-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1808-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1808-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1808-134">See also</span></span>
- [<span data-ttu-id="a1808-135">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1808-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="a1808-136">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="a1808-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="a1808-137">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1808-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
