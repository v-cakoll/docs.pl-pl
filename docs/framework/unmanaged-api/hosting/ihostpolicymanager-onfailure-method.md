---
title: IHostPolicyManager::OnFailure — Metoda
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6277c14901e57e44716911a3ae7dfe1bfe92182a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722331"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="83ed3-102">IHostPolicyManager::OnFailure — Metoda</span><span class="sxs-lookup"><span data-stu-id="83ed3-102">IHostPolicyManager::OnFailure Method</span></span>
<span data-ttu-id="83ed3-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma mieć z akcją określoną przez wywołanie [iclrpolicymanager::setactiononfailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) metody w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.</span><span class="sxs-lookup"><span data-stu-id="83ed3-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83ed3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83ed3-104">Syntax</span></span>  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83ed3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83ed3-105">Parameters</span></span>  
 `failure`  
 <span data-ttu-id="83ed3-106">[in] Jedną z [eclrfailure —](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) wartości, wskazujący rodzaj błędu, do którego odpowiada środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="83ed3-106">[in] One of the [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="83ed3-107">[in] Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, wskazujący akcję CLR trwa w odpowiedzi na `failure`.</span><span class="sxs-lookup"><span data-stu-id="83ed3-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83ed3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="83ed3-108">Return Value</span></span>  
  
|<span data-ttu-id="83ed3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="83ed3-109">HRESULT</span></span>|<span data-ttu-id="83ed3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="83ed3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="83ed3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="83ed3-111">S_OK</span></span>|<span data-ttu-id="83ed3-112">`OnFailure` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="83ed3-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="83ed3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="83ed3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="83ed3-114">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="83ed3-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="83ed3-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="83ed3-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="83ed3-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="83ed3-116">The call timed out.</span></span>|  
|<span data-ttu-id="83ed3-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="83ed3-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="83ed3-118">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="83ed3-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="83ed3-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="83ed3-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="83ed3-120">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="83ed3-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="83ed3-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="83ed3-121">E_FAIL</span></span>|<span data-ttu-id="83ed3-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="83ed3-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="83ed3-123">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="83ed3-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="83ed3-124">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="83ed3-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="83ed3-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83ed3-125">Requirements</span></span>  
 <span data-ttu-id="83ed3-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83ed3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83ed3-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83ed3-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83ed3-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83ed3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83ed3-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83ed3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ed3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83ed3-130">See also</span></span>
- [<span data-ttu-id="83ed3-131">EClrFailure, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="83ed3-131">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="83ed3-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="83ed3-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="83ed3-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="83ed3-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="83ed3-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="83ed3-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
