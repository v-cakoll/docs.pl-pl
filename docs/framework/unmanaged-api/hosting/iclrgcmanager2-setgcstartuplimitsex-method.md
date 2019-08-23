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
ms.openlocfilehash: 0d881c71d4725e1a73d743aa098aecc053182947
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918608"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="13808-102">ICLRGCManager2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="13808-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="13808-103">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="13808-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13808-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="13808-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13808-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="13808-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="13808-106">podczas Określony rozmiar segmentu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="13808-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="13808-107">Minimalny rozmiar segmentu to 4 MB.</span><span class="sxs-lookup"><span data-stu-id="13808-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="13808-108">Segmenty można zwiększyć z przyrostem wynoszącym 1 MB lub większą.</span><span class="sxs-lookup"><span data-stu-id="13808-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="13808-109">podczas Określony maksymalny rozmiar dla generacji 0.</span><span class="sxs-lookup"><span data-stu-id="13808-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="13808-110">Minimalna wielkość generacji 0 to 64 KB.</span><span class="sxs-lookup"><span data-stu-id="13808-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13808-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="13808-111">Return Value</span></span>  
  
|<span data-ttu-id="13808-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13808-112">HRESULT</span></span>|<span data-ttu-id="13808-113">Opis</span><span class="sxs-lookup"><span data-stu-id="13808-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13808-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="13808-114">S_OK</span></span>|<span data-ttu-id="13808-115">`SetGCStartupLimitsEx`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="13808-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="13808-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13808-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13808-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="13808-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13808-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13808-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13808-119">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="13808-119">The call timed out.</span></span>|  
|<span data-ttu-id="13808-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13808-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13808-121">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="13808-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13808-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13808-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13808-123">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="13808-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13808-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13808-124">E_FAIL</span></span>|<span data-ttu-id="13808-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="13808-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13808-126">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="13808-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13808-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="13808-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13808-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13808-128">Remarks</span></span>  
 <span data-ttu-id="13808-129">Wartości, które `SetGCStartupLimitsEx` ustawia się, można określić tylko przed uruchomieniem hosta.</span><span class="sxs-lookup"><span data-stu-id="13808-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="13808-130">Późniejsze wywołania `SetGCStartupLimitsEx` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="13808-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="13808-131">Aby ustawić jeden z parametrów bez wpływu na pozostałe, określ wartość 0 (zero) dla parametru, którego nie chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="13808-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13808-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="13808-132">Requirements</span></span>  
 <span data-ttu-id="13808-133">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13808-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13808-134">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="13808-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13808-135">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="13808-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13808-136">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13808-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13808-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="13808-137">See also</span></span>

- [<span data-ttu-id="13808-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="13808-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="13808-139">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="13808-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="13808-140">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="13808-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="13808-141">ICLRGCManager2, interfejs</span><span class="sxs-lookup"><span data-stu-id="13808-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
