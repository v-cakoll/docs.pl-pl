---
title: "IHostPolicyManager::OnTimeout — Metoda"
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
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b8c29bc281b64368e8b310e2b13f3fcb1bdc6ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="55f6e-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="55f6e-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="55f6e-103">Powiadamia hosta, którego środowisko uruchomieniowe języka wspólnego (CLR) ma mieć z akcją określoną przez wywołanie do [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) metody w odpowiedzi na przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="55f6e-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55f6e-104">Syntax</span></span>  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55f6e-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="55f6e-106">[in] Jeden z [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wartości i wskazujący rodzaj operacji został przekroczony.</span><span class="sxs-lookup"><span data-stu-id="55f6e-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="55f6e-107">[in] Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości i wskazujący akcję CLR trwa w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="55f6e-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f6e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="55f6e-108">Return Value</span></span>  
  
|<span data-ttu-id="55f6e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55f6e-109">HRESULT</span></span>|<span data-ttu-id="55f6e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="55f6e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55f6e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="55f6e-111">S_OK</span></span>|<span data-ttu-id="55f6e-112">`OnTimeout`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="55f6e-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="55f6e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="55f6e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="55f6e-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="55f6e-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="55f6e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="55f6e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="55f6e-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="55f6e-116">The call timed out.</span></span>|  
|<span data-ttu-id="55f6e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="55f6e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="55f6e-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="55f6e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="55f6e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="55f6e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="55f6e-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="55f6e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="55f6e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55f6e-121">E_FAIL</span></span>|<span data-ttu-id="55f6e-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="55f6e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="55f6e-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="55f6e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="55f6e-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="55f6e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55f6e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55f6e-125">Requirements</span></span>  
 <span data-ttu-id="55f6e-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f6e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f6e-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="55f6e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55f6e-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="55f6e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55f6e-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f6e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f6e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="55f6e-130">See Also</span></span>  
 [<span data-ttu-id="55f6e-131">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55f6e-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="55f6e-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="55f6e-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="55f6e-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="55f6e-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="55f6e-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="55f6e-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
