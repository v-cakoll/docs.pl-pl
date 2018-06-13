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
ms.openlocfilehash: 187c0a8d929958b7eaf1e99771da6a0d29c3d5f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434190"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="b1b17-102">ICLRMemoryNotificationCallback::OnMemoryNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1b17-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="b1b17-103">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b1b17-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1b17-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1b17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1b17-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="b1b17-106">[in] Jeden z [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) wartości, wskazując wykorzystania pamięci komputera występują.</span><span class="sxs-lookup"><span data-stu-id="b1b17-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1b17-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b1b17-107">Return Value</span></span>  
  
|<span data-ttu-id="b1b17-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1b17-108">HRESULT</span></span>|<span data-ttu-id="b1b17-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b1b17-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1b17-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1b17-110">S_OK</span></span>|<span data-ttu-id="b1b17-111">`OnMemoryNotification` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b1b17-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="b1b17-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1b17-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1b17-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="b1b17-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1b17-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1b17-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1b17-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="b1b17-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1b17-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1b17-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1b17-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b1b17-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1b17-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1b17-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1b17-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="b1b17-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1b17-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1b17-120">E_FAIL</span></span>|<span data-ttu-id="b1b17-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="b1b17-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1b17-122">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="b1b17-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1b17-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1b17-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1b17-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1b17-124">Remarks</span></span>  
 <span data-ttu-id="b1b17-125">Środowisko CLR rejestruje wywołanie zwrotne do `OnMemoryNotification` za pomocą wywołania [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b1b17-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="b1b17-126">Środowisko uruchomieniowe używa informacji zwrócony podczas wywołania zwrotnego zwolnienia dodatkowej pamięci, gdy host raportów pamięci, które bardzo mało zasobów.</span><span class="sxs-lookup"><span data-stu-id="b1b17-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1b17-127">Wywołuje się `OnMemoryNotification` nigdy nie blokuj.</span><span class="sxs-lookup"><span data-stu-id="b1b17-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="b1b17-128">Zawsze zwracają natychmiast.</span><span class="sxs-lookup"><span data-stu-id="b1b17-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1b17-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1b17-129">Requirements</span></span>  
 <span data-ttu-id="b1b17-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b17-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b17-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1b17-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1b17-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1b17-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1b17-133">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b17-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b17-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1b17-134">See Also</span></span>  
 [<span data-ttu-id="b1b17-135">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1b17-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="b1b17-136">RegisterMemoryNotificationCallback, metoda</span><span class="sxs-lookup"><span data-stu-id="b1b17-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="b1b17-137">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1b17-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
