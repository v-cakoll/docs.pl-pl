---
title: ICLRGCManager::SetGCStartupLimits — Metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ffbe29db96cbb6162adc3b4cc77b45dcef27a46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117290"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="f7657-102">ICLRGCManager::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7657-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="f7657-103">Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="f7657-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f7657-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można ustawić rozmiar segmentu i rozmiar maksymalny generacji 0 do wartości większej niż `DWORD` przy użyciu [iclrgcmanager2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f7657-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7657-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7657-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7657-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7657-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="f7657-107">[in] Określony rozmiar segmentu kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="f7657-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="f7657-108">Rozmiar minimalny segmentu jest 4 MB.</span><span class="sxs-lookup"><span data-stu-id="f7657-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="f7657-109">Segmenty może być zwiększonej w przyrostach co 1 MB lub większy.</span><span class="sxs-lookup"><span data-stu-id="f7657-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="f7657-110">[in] Określony maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="f7657-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="f7657-111">Rozmiar minimalny generacji 0 wynosi 64 KB.</span><span class="sxs-lookup"><span data-stu-id="f7657-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7657-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f7657-112">Return Value</span></span>  
  
|<span data-ttu-id="f7657-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7657-113">HRESULT</span></span>|<span data-ttu-id="f7657-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f7657-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7657-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7657-115">S_OK</span></span>|`SetGCStartupLimits` <span data-ttu-id="f7657-116">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f7657-116">returned successfully.</span></span>|  
|<span data-ttu-id="f7657-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7657-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7657-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7657-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7657-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7657-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7657-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7657-120">The call timed out.</span></span>|  
|<span data-ttu-id="f7657-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7657-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7657-122">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="f7657-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7657-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7657-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7657-124">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="f7657-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7657-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7657-125">E_FAIL</span></span>|<span data-ttu-id="f7657-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f7657-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7657-127">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f7657-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7657-128">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7657-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7657-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7657-129">Remarks</span></span>  
 <span data-ttu-id="f7657-130">Wartości, `SetGCStartupLimits` zestawów, które może zostać określony tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f7657-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="f7657-131">Późniejsze wywołania `SetGCStartupLimits` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f7657-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7657-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7657-132">Requirements</span></span>  
 <span data-ttu-id="f7657-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7657-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7657-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7657-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7657-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7657-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f7657-136">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f7657-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7657-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7657-137">See also</span></span>

- [<span data-ttu-id="f7657-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="f7657-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="f7657-139">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="f7657-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="f7657-140">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f7657-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="f7657-141">ICLRGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f7657-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
