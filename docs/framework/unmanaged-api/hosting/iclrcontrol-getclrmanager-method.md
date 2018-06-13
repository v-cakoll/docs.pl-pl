---
title: ICLRControl::GetCLRManager — Metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f375afde247c3a9b95e1220df747d3f2b95e2840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436432"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="5e75b-102">ICLRControl::GetCLRManager — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e75b-102">ICLRControl::GetCLRManager Method</span></span>
<span data-ttu-id="5e75b-103">Pobiera wskaźnika interfejsu do wystąpienia dowolnego typu menedżera, która hosta można użyć do skonfigurowania środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="5e75b-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e75b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e75b-104">Syntax</span></span>  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e75b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e75b-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="5e75b-106">[in] `IID` Typu Menedżera do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="5e75b-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="5e75b-107">Następujące `IID` wartości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5e75b-107">The following `IID` values are supported.</span></span>  
  
-   <span data-ttu-id="5e75b-108">IID_ICLRDebugManager: Określa, że `ppObject` będzie typu [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-109">IID_ICLRErrorReportingManager: Określa, że `ppObject` będzie typu [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-110">IID_ICLRGCManager: Określa, że `ppObject` będzie typu [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-111">IID_ICLRHostProtectionManager: Określa, że `ppObject` będzie typu [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-112">IID_ICLROnEventManager: Określa, że `ppObject` będzie typu [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-113">IID_ICLRPolicyManager: Określa, że `ppObject` będzie typu [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>  
  
-   <span data-ttu-id="5e75b-114">IID_ICLRTaskManager: speciries który `ppObject` będzie typu [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-114">IID_ICLRTaskManager: speciries that `ppObject` will be of type [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="5e75b-115">[out] Wskaźnik interfejsu Menedżera żądanego lub wartość null, jeśli zażądano typ Menedżera nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="5e75b-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e75b-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e75b-116">Return Value</span></span>  
  
|<span data-ttu-id="5e75b-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e75b-117">HRESULT</span></span>|<span data-ttu-id="5e75b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="5e75b-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e75b-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e75b-119">S_OK</span></span>|<span data-ttu-id="5e75b-120">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5e75b-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="5e75b-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e75b-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e75b-122">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e75b-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5e75b-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5e75b-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5e75b-124">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e75b-124">The call timed out.</span></span>|  
|<span data-ttu-id="5e75b-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5e75b-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5e75b-126">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="5e75b-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5e75b-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5e75b-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5e75b-128">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="5e75b-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5e75b-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e75b-129">E_FAIL</span></span>|<span data-ttu-id="5e75b-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="5e75b-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5e75b-131">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="5e75b-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5e75b-132">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5e75b-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e75b-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="5e75b-133">E_NOINTERFACE</span></span>|<span data-ttu-id="5e75b-134">Typ interfejsu nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="5e75b-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e75b-135">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e75b-135">Requirements</span></span>  
 <span data-ttu-id="5e75b-136">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e75b-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e75b-137">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e75b-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e75b-138">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e75b-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e75b-139">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e75b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e75b-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e75b-140">See Also</span></span>  
 [<span data-ttu-id="5e75b-141">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e75b-141">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="5e75b-142">IHostControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e75b-142">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
