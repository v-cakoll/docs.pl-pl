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
ms.openlocfilehash: f9d6c4f01b01944c885190f90e2195c3a308490a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141207"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="6ae3f-102">ICLRGCManager::SetGCStartupLimits — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ae3f-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="6ae3f-103">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6ae3f-104">Począwszy od .NET Framework 4,5, można ustawić rozmiar segmentu i rozmiar maksymalnej generacji 0 na wartość większą niż `DWORD` przy użyciu metody [ICLRGCManager2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6ae3f-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ae3f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ae3f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ae3f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ae3f-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="6ae3f-107">podczas Określony rozmiar segmentu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="6ae3f-108">Minimalny rozmiar segmentu to 4 MB.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="6ae3f-109">Segmenty można zwiększyć z przyrostem wynoszącym 1 MB lub większą.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="6ae3f-110">podczas Określony maksymalny rozmiar dla generacji 0.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="6ae3f-111">Minimalna wielkość generacji 0 to 64 KB.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ae3f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6ae3f-112">Return Value</span></span>  
  
|<span data-ttu-id="6ae3f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6ae3f-113">HRESULT</span></span>|<span data-ttu-id="6ae3f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6ae3f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6ae3f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6ae3f-115">S_OK</span></span>|<span data-ttu-id="6ae3f-116">`SetGCStartupLimits` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="6ae3f-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6ae3f-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6ae3f-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6ae3f-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6ae3f-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6ae3f-120">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-120">The call timed out.</span></span>|  
|<span data-ttu-id="6ae3f-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6ae3f-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6ae3f-122">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6ae3f-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6ae3f-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6ae3f-124">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6ae3f-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6ae3f-125">E_FAIL</span></span>|<span data-ttu-id="6ae3f-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6ae3f-127">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6ae3f-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ae3f-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ae3f-129">Remarks</span></span>  
 <span data-ttu-id="6ae3f-130">Wartości, które `SetGCStartupLimits` zestawy, można określić tylko raz.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="6ae3f-131">Późniejsze wywołania `SetGCStartupLimits` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="6ae3f-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ae3f-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ae3f-132">Requirements</span></span>  
 <span data-ttu-id="6ae3f-133">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ae3f-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ae3f-134">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ae3f-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ae3f-135">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ae3f-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ae3f-136">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ae3f-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ae3f-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ae3f-137">See also</span></span>

- [<span data-ttu-id="6ae3f-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="6ae3f-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="6ae3f-139">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="6ae3f-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="6ae3f-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ae3f-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="6ae3f-141">ICLRGCManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ae3f-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
