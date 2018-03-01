---
title: "IHostControl::GetHostManager — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6701350fa9bdb51843b117b0191b677e739807a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcontrolgethostmanager-method"></a><span data-ttu-id="cdbee-102">IHostControl::GetHostManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="cdbee-102">IHostControl::GetHostManager Method</span></span>
<span data-ttu-id="cdbee-103">Pobiera wskaźnika interfejsu hosta implementacji interfejsu z określonym `IID`.</span><span class="sxs-lookup"><span data-stu-id="cdbee-103">Gets an interface pointer to the host's implementation of the interface with the specified `IID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdbee-104">Syntax</span></span>  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdbee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdbee-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="cdbee-106">[in] `IID` Interfejsu, który jest wyszukiwanie środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="cdbee-106">[in] The `IID` of the interface that the common language runtime (CLR) is querying for.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="cdbee-107">[out] Wskaźnik do interfejsu zaimplementowana hosta lub wartość null, jeśli host nie obsługuje tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cdbee-107">[out] A pointer to the host-implemented interface, or null if the host does not support this interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdbee-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdbee-108">Return Value</span></span>  
  
|<span data-ttu-id="cdbee-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdbee-109">HRESULT</span></span>|<span data-ttu-id="cdbee-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cdbee-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdbee-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cdbee-111">S_OK</span></span>|<span data-ttu-id="cdbee-112">`GetHostManager`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cdbee-112">`GetHostManager` returned successfully.</span></span>|  
|<span data-ttu-id="cdbee-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cdbee-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cdbee-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="cdbee-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cdbee-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cdbee-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cdbee-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="cdbee-116">The call timed out.</span></span>|  
|<span data-ttu-id="cdbee-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cdbee-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cdbee-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="cdbee-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cdbee-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cdbee-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cdbee-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="cdbee-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cdbee-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cdbee-121">E_FAIL</span></span>|<span data-ttu-id="cdbee-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="cdbee-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cdbee-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="cdbee-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cdbee-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cdbee-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cdbee-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cdbee-125">E_INVALIDARG</span></span>|<span data-ttu-id="cdbee-126">Żądany `IID` jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="cdbee-126">The requested `IID` is not valid.</span></span>|  
|<span data-ttu-id="cdbee-127">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="cdbee-127">E_NOINTERFACE</span></span>|<span data-ttu-id="cdbee-128">Żądany interfejs nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="cdbee-128">The requested interface is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdbee-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdbee-129">Remarks</span></span>  
 <span data-ttu-id="cdbee-130">Środowisko CLR wysyła zapytanie do hosta, aby ustalić, czy obsługuje co najmniej jednego z poniższych interfejsów:</span><span class="sxs-lookup"><span data-stu-id="cdbee-130">The CLR queries the host to determine whether it supports one or more of the following interfaces:</span></span>  
  
-   [<span data-ttu-id="cdbee-131">IHostMemoryManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-131">IHostMemoryManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-132">IHostTaskManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-132">IHostTaskManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-133">IHostThreadPoolManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-133">IHostThreadPoolManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-134">IHostIoCompletionManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-134">IHostIoCompletionManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-135">IHostSyncManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-135">IHostSyncManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-136">IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-136">IHostAssemblyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-137">IHostGCManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-137">IHostGCManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-138">IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-138">IHostPolicyManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [<span data-ttu-id="cdbee-139">IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="cdbee-139">IHostSecurityManager</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 <span data-ttu-id="cdbee-140">Jeśli host obsługuje określonego interfejsu, ustawia `ppObject` jego implementację tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cdbee-140">If the host supports the specified interface, it sets `ppObject` to its implementation of that interface.</span></span> <span data-ttu-id="cdbee-141">W przeciwnym razie ustawia `ppObject` na wartość null.</span><span class="sxs-lookup"><span data-stu-id="cdbee-141">Otherwise, it sets `ppObject` to null.</span></span>  
  
 <span data-ttu-id="cdbee-142">Środowisko CLR nie wywołuje `Release` menedżerów hosta, nawet wtedy, gdy została ona zamknięta.</span><span class="sxs-lookup"><span data-stu-id="cdbee-142">The CLR does not call `Release` on host managers, even when you shut it down.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdbee-143">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdbee-143">Requirements</span></span>  
 <span data-ttu-id="cdbee-144">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbee-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbee-145">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cdbee-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdbee-146">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cdbee-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbee-147">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbee-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbee-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdbee-148">See Also</span></span>  
 [<span data-ttu-id="cdbee-149">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdbee-149">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
