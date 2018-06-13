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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d68790cdb671efdd0761ceef59196e8646654d5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439610"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="fd899-102">IHostMemoryManager::RegisterMemoryNotificationCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd899-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="fd899-103">Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta powiadomiono środowisko uruchomieniowe języka wspólnego (CLR) z bieżącego obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="fd899-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd899-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd899-104">Syntax</span></span>  
  
```  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd899-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd899-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="fd899-106">[in] Wskaźnik interfejsu do [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) wystąpienia, który jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="fd899-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd899-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fd899-107">Return Value</span></span>  
  
|<span data-ttu-id="fd899-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fd899-108">HRESULT</span></span>|<span data-ttu-id="fd899-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fd899-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fd899-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fd899-110">S_OK</span></span>|<span data-ttu-id="fd899-111">`RegisterMemoryNotificationCallback` zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="fd899-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="fd899-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fd899-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fd899-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fd899-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fd899-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fd899-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fd899-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fd899-115">The call timed out.</span></span>|  
|<span data-ttu-id="fd899-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fd899-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fd899-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="fd899-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fd899-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fd899-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fd899-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="fd899-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fd899-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fd899-120">E_FAIL</span></span>|<span data-ttu-id="fd899-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fd899-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fd899-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fd899-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fd899-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fd899-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd899-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd899-124">Remarks</span></span>  
 <span data-ttu-id="fd899-125">Ponieważ `ICLRMemoryNotificationCallback` interfejs definiuje tylko jedną metodę ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)) i dlatego `pCallback` jest wskaźnikiem do `ICLRMemoryNotificationCallback` podane przez środowisko CLR, wystąpienie Rejestracja jest skutecznie dla samej siebie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="fd899-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="fd899-126">Wywołuje hosta `OnMemoryNotification` warunków braku pamięci raportu, a nie przy użyciu standardowych Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="fd899-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="fd899-127">Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fd899-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd899-128">Wywołuje się `OnMemoryNotification` nigdy nie blokuj.</span><span class="sxs-lookup"><span data-stu-id="fd899-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="fd899-129">Zawsze zwracają natychmiast.</span><span class="sxs-lookup"><span data-stu-id="fd899-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd899-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd899-130">Requirements</span></span>  
 <span data-ttu-id="fd899-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd899-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd899-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fd899-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd899-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd899-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd899-134">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd899-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd899-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd899-135">See Also</span></span>  
 [<span data-ttu-id="fd899-136">ICLRMemoryNotificationCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd899-136">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [<span data-ttu-id="fd899-137">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd899-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
