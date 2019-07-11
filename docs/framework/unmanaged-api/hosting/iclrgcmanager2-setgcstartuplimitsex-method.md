---
title: ICLRGCManager2::SetGCStartupLimitsEx — Metoda
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 356678afb537ab5e5e1653c4f71140ce704e55ef
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779682"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="645fb-102">ICLRGCManager2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="645fb-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="645fb-103">Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="645fb-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="645fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="645fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="645fb-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="645fb-106">[in] Określony rozmiar segmentu kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="645fb-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="645fb-107">Rozmiar minimalny segmentu jest 4 MB.</span><span class="sxs-lookup"><span data-stu-id="645fb-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="645fb-108">Segmenty może być zwiększonej w przyrostach co 1 MB lub większy.</span><span class="sxs-lookup"><span data-stu-id="645fb-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="645fb-109">[in] Określony maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="645fb-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="645fb-110">Rozmiar minimalny generacji 0 wynosi 64 KB.</span><span class="sxs-lookup"><span data-stu-id="645fb-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="645fb-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="645fb-111">Return Value</span></span>  
  
|<span data-ttu-id="645fb-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="645fb-112">HRESULT</span></span>|<span data-ttu-id="645fb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="645fb-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="645fb-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="645fb-114">S_OK</span></span>|<span data-ttu-id="645fb-115">`SetGCStartupLimitsEx` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="645fb-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="645fb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="645fb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="645fb-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="645fb-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="645fb-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="645fb-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="645fb-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="645fb-119">The call timed out.</span></span>|  
|<span data-ttu-id="645fb-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="645fb-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="645fb-121">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="645fb-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="645fb-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="645fb-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="645fb-123">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="645fb-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="645fb-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="645fb-124">E_FAIL</span></span>|<span data-ttu-id="645fb-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="645fb-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="645fb-126">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="645fb-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="645fb-127">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="645fb-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="645fb-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="645fb-128">Remarks</span></span>  
 <span data-ttu-id="645fb-129">Wartości, `SetGCStartupLimitsEx` zestawy można określić tylko, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="645fb-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="645fb-130">Późniejsze wywołania `SetGCStartupLimitsEx` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="645fb-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="645fb-131">Aby ustawić albo parametr bez wpływu na drugi, należy określić 0 (zero) dla parametru, których nie chcesz, aby zmienić.</span><span class="sxs-lookup"><span data-stu-id="645fb-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="645fb-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="645fb-132">Requirements</span></span>  
 <span data-ttu-id="645fb-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="645fb-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="645fb-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="645fb-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="645fb-135">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="645fb-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="645fb-136">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="645fb-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645fb-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="645fb-137">See also</span></span>

- [<span data-ttu-id="645fb-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="645fb-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="645fb-139">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="645fb-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="645fb-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="645fb-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="645fb-141">ICLRGCManager2, interfejs</span><span class="sxs-lookup"><span data-stu-id="645fb-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
