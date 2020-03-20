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
ms.openlocfilehash: 9885149a71147db6eef13958b8ef825caa1d6ec6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176386"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="b554b-102">ICLRGCManager2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="b554b-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="b554b-103">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b554b-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b554b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b554b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b554b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b554b-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="b554b-106">[w] Określony rozmiar segmentu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="b554b-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="b554b-107">Minimalny rozmiar segmentu to 4 MB.</span><span class="sxs-lookup"><span data-stu-id="b554b-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="b554b-108">Segmenty można zwiększać w przyrostach co 1 MB lub większych.</span><span class="sxs-lookup"><span data-stu-id="b554b-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="b554b-109">[w] Określony maksymalny rozmiar dla generacji 0.</span><span class="sxs-lookup"><span data-stu-id="b554b-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="b554b-110">Minimalna generacja 0 rozmiar jest 64 KB.</span><span class="sxs-lookup"><span data-stu-id="b554b-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b554b-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b554b-111">Return Value</span></span>  
  
|<span data-ttu-id="b554b-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b554b-112">HRESULT</span></span>|<span data-ttu-id="b554b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b554b-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b554b-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="b554b-114">S_OK</span></span>|<span data-ttu-id="b554b-115">`SetGCStartupLimitsEx`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b554b-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="b554b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b554b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b554b-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b554b-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b554b-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b554b-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b554b-119">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="b554b-119">The call timed out.</span></span>|  
|<span data-ttu-id="b554b-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b554b-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b554b-121">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="b554b-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b554b-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b554b-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b554b-123">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="b554b-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b554b-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="b554b-124">E_FAIL</span></span>|<span data-ttu-id="b554b-125">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="b554b-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b554b-126">Po metoda zwraca E_FAIL, CLR nie jest już użyteczny w procesie.</span><span class="sxs-lookup"><span data-stu-id="b554b-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b554b-127">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b554b-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b554b-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b554b-128">Remarks</span></span>  
 <span data-ttu-id="b554b-129">Wartości, `SetGCStartupLimitsEx` które ustawia można określić tylko przed rozpoczęciem hosta.</span><span class="sxs-lookup"><span data-stu-id="b554b-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="b554b-130">Późniejsze `SetGCStartupLimitsEx` wywołania są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="b554b-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="b554b-131">Aby ustawić jeden z tych parametrów bez wpływu na drugi, określ 0 (zero) dla parametru, którego nie chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="b554b-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b554b-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b554b-132">Requirements</span></span>  
 <span data-ttu-id="b554b-133">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b554b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b554b-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b554b-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b554b-135">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b554b-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b554b-136">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b554b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b554b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b554b-137">See also</span></span>

- [<span data-ttu-id="b554b-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="b554b-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="b554b-139">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="b554b-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="b554b-140">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b554b-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="b554b-141">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b554b-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)
