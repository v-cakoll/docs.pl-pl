---
title: IHostTaskManager::SetCLRTaskManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: c674cc43065bf8ea102bec1c5134757380454913
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141228"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="ec896-102">IHostTaskManager::SetCLRTaskManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec896-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="ec896-103">Udostępnia host ze wskaźnikiem interfejsu do wystąpienia [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) zaimplementowanego przez środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="ec896-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec896-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec896-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec896-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec896-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="ec896-106">podczas Wskaźnik do wystąpienia `ICLRTaskManager` implementowanego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ec896-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec896-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ec896-107">Return Value</span></span>  
  
|<span data-ttu-id="ec896-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec896-108">HRESULT</span></span>|<span data-ttu-id="ec896-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ec896-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ec896-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ec896-110">S_OK</span></span>|<span data-ttu-id="ec896-111">`SetCLRTaskManager` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="ec896-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="ec896-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ec896-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ec896-113">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ec896-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ec896-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ec896-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ec896-115">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ec896-115">The call timed out.</span></span>|  
|<span data-ttu-id="ec896-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ec896-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ec896-117">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ec896-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ec896-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ec896-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ec896-119">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ec896-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ec896-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ec896-120">E_FAIL</span></span>|<span data-ttu-id="ec896-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ec896-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ec896-122">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="ec896-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ec896-123">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ec896-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec896-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec896-124">Remarks</span></span>  
 <span data-ttu-id="ec896-125">Wywołania środowiska uruchomieniowego `SetCLRTaskManager`, aby dostarczyć host ze wskaźnikiem interfejsu do wystąpienia `ICLRTaskManager`.</span><span class="sxs-lookup"><span data-stu-id="ec896-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec896-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec896-126">Requirements</span></span>  
 <span data-ttu-id="ec896-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec896-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec896-128">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ec896-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ec896-129">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ec896-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec896-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec896-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec896-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec896-131">See also</span></span>

- [<span data-ttu-id="ec896-132">ICLRTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec896-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ec896-133">ICLRTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec896-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ec896-134">IHostTask, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec896-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ec896-135">IHostTaskManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec896-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
