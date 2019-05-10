---
title: IHostControl::GetHostManager — Metoda
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e51ff24698a2839972f9a36eac6c18d4f6709ebd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600152"
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="a14a0-102">IHostControl::GetHostManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="a14a0-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="a14a0-103">Pobiera wskaźnik interfejsu do implementacji interfejsu hosta z określonym `IID`.</span><span class="sxs-lookup"><span data-stu-id="a14a0-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a14a0-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a14a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a14a0-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="a14a0-106">[in] `IID` Interfejsu, który wyszukuje jest środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a14a0-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="a14a0-107">[out] Wskaźnik do interfejsu implementowany przez hosta lub wartość null, jeśli host nie obsługuje tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a14a0-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a14a0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a14a0-108">Return Value</span></span>  
  
|<span data-ttu-id="a14a0-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a14a0-109">HRESULT</span></span>|<span data-ttu-id="a14a0-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a14a0-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a14a0-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a14a0-111">S_OK</span></span>|<span data-ttu-id="a14a0-112">`GetHostManager` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="a14a0-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="a14a0-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a14a0-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a14a0-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a14a0-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a14a0-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a14a0-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a14a0-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="a14a0-116">The call timed out.</span></span>|  
|<span data-ttu-id="a14a0-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a14a0-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a14a0-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="a14a0-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a14a0-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a14a0-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a14a0-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="a14a0-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a14a0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a14a0-121">E_FAIL</span></span>|<span data-ttu-id="a14a0-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a14a0-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a14a0-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="a14a0-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a14a0-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a14a0-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a14a0-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a14a0-125">E_INVALIDARG</span></span>|<span data-ttu-id="a14a0-126">Żądany `IID` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="a14a0-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="a14a0-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="a14a0-127">E_NOINTERFACE</span></span>|<span data-ttu-id="a14a0-128">Żądany interfejs nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="a14a0-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a14a0-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a14a0-129">Remarks</span></span>  
 <span data-ttu-id="a14a0-130">Środowisko CLR wykonuje kwerendę hostowi na określenie, czy obsługuje co najmniej jeden z poniższych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="a14a0-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
- [<span data-ttu-id="a14a0-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
- [<span data-ttu-id="a14a0-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
- [<span data-ttu-id="a14a0-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
- [<span data-ttu-id="a14a0-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
- [<span data-ttu-id="a14a0-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
- [<span data-ttu-id="a14a0-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
- [<span data-ttu-id="a14a0-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
- [<span data-ttu-id="a14a0-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
- [<span data-ttu-id="a14a0-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="a14a0-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="a14a0-140">Jeśli host obsługuje określonego interfejsu, ustawia `ppObject` do jej implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a14a0-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="a14a0-141">W przeciwnym wypadku ustawia `ppObject` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="a14a0-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="a14a0-142">Środowisko CLR wywołuje `Release` na hoście menedżerów, nawet wtedy, gdy zostanie ona zamknięta.</span><span class="sxs-lookup"><span data-stu-id="a14a0-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a14a0-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a14a0-143">Requirements</span></span>  
 <span data-ttu-id="a14a0-144">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a14a0-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a14a0-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a14a0-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a14a0-146">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a14a0-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a14a0-147">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a14a0-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a14a0-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a14a0-148">See also</span></span>

- [<span data-ttu-id="a14a0-149">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="a14a0-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
