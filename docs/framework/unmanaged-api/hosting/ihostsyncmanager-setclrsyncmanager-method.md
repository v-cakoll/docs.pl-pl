---
title: IHostSyncManager::SetCLRSyncManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 9c08a790d4dad748e5d09271bd870add22255b4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132613"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="f58fb-102">IHostSyncManager::SetCLRSyncManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="f58fb-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="f58fb-103">Ustawia wystąpienie [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) do skojarzenia z bieżącym wystąpieniem [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f58fb-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f58fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f58fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f58fb-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="f58fb-106">podczas Wskaźnik do wystąpienia `ICLRSyncManager` dostarczonego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="f58fb-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f58fb-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f58fb-107">Return Value</span></span>  
  
|<span data-ttu-id="f58fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f58fb-108">HRESULT</span></span>|<span data-ttu-id="f58fb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f58fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f58fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f58fb-110">S_OK</span></span>|<span data-ttu-id="f58fb-111">`SetCLRSyncManager` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="f58fb-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="f58fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f58fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f58fb-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f58fb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f58fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f58fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f58fb-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="f58fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="f58fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f58fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f58fb-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="f58fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f58fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f58fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f58fb-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="f58fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f58fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f58fb-120">E_FAIL</span></span>|<span data-ttu-id="f58fb-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f58fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f58fb-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="f58fb-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f58fb-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f58fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f58fb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f58fb-124">Remarks</span></span>  
 <span data-ttu-id="f58fb-125">W celu ułatwienia komunikacji między hostem i środowiskiem CLR Interfejsy hostingu zwykle są parami.</span><span class="sxs-lookup"><span data-stu-id="f58fb-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="f58fb-126">Jeden element członkowski pary jest implementowany przez hosta, a drugi element członkowski jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f58fb-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="f58fb-127">Jako implementacja po stronie hosta interfejs `IHostSyncManager` odpowiada interfejsowi `ICLRSyncManager` zaimplementowanym przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="f58fb-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="f58fb-128">Wywołania CLR `SetCLRSyncManager`, aby dostarczyć wystąpienie `ICLRSyncManager` dla hosta do skojarzenia z bieżącym wystąpieniem `IHostSyncManager`.</span><span class="sxs-lookup"><span data-stu-id="f58fb-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f58fb-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f58fb-129">Requirements</span></span>  
 <span data-ttu-id="f58fb-130">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f58fb-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f58fb-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f58fb-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f58fb-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f58fb-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f58fb-133">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f58fb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f58fb-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f58fb-134">See also</span></span>

- [<span data-ttu-id="f58fb-135">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f58fb-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f58fb-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f58fb-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
