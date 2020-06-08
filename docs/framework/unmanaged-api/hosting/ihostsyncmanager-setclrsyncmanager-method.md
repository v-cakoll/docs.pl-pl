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
ms.openlocfilehash: 7f1832b22a1b80855f48eba6d39bff64da6fa5f9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501446"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="2983c-102">IHostSyncManager::SetCLRSyncManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="2983c-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="2983c-103">Ustawia wystąpienie [ICLRSyncManager](iclrsyncmanager-interface.md) do skojarzenia z bieżącym wystąpieniem [IHostSyncManager](ihostsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2983c-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2983c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2983c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2983c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2983c-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="2983c-106">podczas Wskaźnik do `ICLRSyncManager` wystąpienia dostarczonego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2983c-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2983c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2983c-107">Return Value</span></span>  
  
|<span data-ttu-id="2983c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2983c-108">HRESULT</span></span>|<span data-ttu-id="2983c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2983c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2983c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2983c-110">S_OK</span></span>|<span data-ttu-id="2983c-111">`SetCLRSyncManager`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="2983c-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="2983c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2983c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2983c-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2983c-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2983c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2983c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2983c-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="2983c-115">The call timed out.</span></span>|  
|<span data-ttu-id="2983c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2983c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2983c-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="2983c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2983c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2983c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2983c-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="2983c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2983c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2983c-120">E_FAIL</span></span>|<span data-ttu-id="2983c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="2983c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2983c-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2983c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2983c-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2983c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2983c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2983c-124">Remarks</span></span>  
 <span data-ttu-id="2983c-125">W celu ułatwienia komunikacji między hostem i środowiskiem CLR Interfejsy hostingu zwykle są parami.</span><span class="sxs-lookup"><span data-stu-id="2983c-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="2983c-126">Jeden element członkowski pary jest implementowany przez hosta, a drugi element członkowski jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="2983c-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="2983c-127">Jako implementacja po stronie hosta `IHostSyncManager` interfejs odpowiada `ICLRSyncManager` interfejsowi zaimplementowanemu przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="2983c-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="2983c-128">Środowisko CLR wywołuje w `SetCLRSyncManager` celu dostarczenia `ICLRSyncManager` wystąpienia hosta do skojarzenia z bieżącym `IHostSyncManager` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="2983c-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2983c-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2983c-129">Requirements</span></span>  
 <span data-ttu-id="2983c-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2983c-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2983c-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2983c-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2983c-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2983c-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2983c-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2983c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2983c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2983c-134">See also</span></span>

- [<span data-ttu-id="2983c-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2983c-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2983c-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="2983c-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
