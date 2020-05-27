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
ms.openlocfilehash: bbeae2561d2d340c1a7dfed38e740dcc6838e4da
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803094"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="a76fa-102">IHostSyncManager::SetCLRSyncManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="a76fa-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="a76fa-103">Ustawia wystąpienie [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) do skojarzenia z bieżącym wystąpieniem [IHostSyncManager](ihostsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a76fa-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a76fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a76fa-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a76fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a76fa-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="a76fa-106">podczas Wskaźnik do `ICLRSyncManager` wystąpienia dostarczonego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a76fa-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a76fa-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a76fa-107">Return Value</span></span>  
  
|<span data-ttu-id="a76fa-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a76fa-108">HRESULT</span></span>|<span data-ttu-id="a76fa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a76fa-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a76fa-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a76fa-110">S_OK</span></span>|<span data-ttu-id="a76fa-111">`SetCLRSyncManager`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="a76fa-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="a76fa-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a76fa-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a76fa-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a76fa-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a76fa-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a76fa-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a76fa-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a76fa-115">The call timed out.</span></span>|  
|<span data-ttu-id="a76fa-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a76fa-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a76fa-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a76fa-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a76fa-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a76fa-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a76fa-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a76fa-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a76fa-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a76fa-120">E_FAIL</span></span>|<span data-ttu-id="a76fa-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a76fa-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a76fa-122">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="a76fa-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a76fa-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a76fa-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a76fa-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a76fa-124">Remarks</span></span>  
 <span data-ttu-id="a76fa-125">W celu ułatwienia komunikacji między hostem i środowiskiem CLR Interfejsy hostingu zwykle są parami.</span><span class="sxs-lookup"><span data-stu-id="a76fa-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="a76fa-126">Jeden element członkowski pary jest implementowany przez hosta, a drugi element członkowski jest implementowany przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a76fa-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="a76fa-127">Jako implementacja po stronie hosta `IHostSyncManager` interfejs odpowiada `ICLRSyncManager` interfejsowi zaimplementowanemu przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="a76fa-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="a76fa-128">Środowisko CLR wywołuje w `SetCLRSyncManager` celu dostarczenia `ICLRSyncManager` wystąpienia hosta do skojarzenia z bieżącym `IHostSyncManager` wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="a76fa-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a76fa-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a76fa-129">Requirements</span></span>  
 <span data-ttu-id="a76fa-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a76fa-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a76fa-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a76fa-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a76fa-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a76fa-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a76fa-133">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a76fa-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a76fa-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a76fa-134">See also</span></span>

- [<span data-ttu-id="a76fa-135">ICLRSyncManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a76fa-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a76fa-136">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a76fa-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
