---
title: IHostPolicyManager::OnTimeout — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: d5b5fa5198ae2c0bba30ae0f8d6d3834f2891672
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178002"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="9765c-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="9765c-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="9765c-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma zamiar podjąć akcję określoną przez wywołanie [do metody ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="9765c-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9765c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9765c-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9765c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9765c-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="9765c-106">[w] Jedna z wartości [EClrOperation,](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) wskazująca rodzaj operacji, która się przesunęła.</span><span class="sxs-lookup"><span data-stu-id="9765c-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="9765c-107">[w] Jedną z wartości [EPolicyAction,](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wskazując akcję, którą clr podejmuje w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="9765c-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9765c-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9765c-108">Return Value</span></span>  
  
|<span data-ttu-id="9765c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9765c-109">HRESULT</span></span>|<span data-ttu-id="9765c-110">Opis</span><span class="sxs-lookup"><span data-stu-id="9765c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9765c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="9765c-111">S_OK</span></span>|<span data-ttu-id="9765c-112">`OnTimeout`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9765c-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="9765c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9765c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9765c-114">Clr nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9765c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9765c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9765c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9765c-116">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9765c-116">The call timed out.</span></span>|  
|<span data-ttu-id="9765c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9765c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9765c-118">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="9765c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9765c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9765c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9765c-120">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="9765c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9765c-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="9765c-121">E_FAIL</span></span>|<span data-ttu-id="9765c-122">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="9765c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9765c-123">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="9765c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9765c-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9765c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9765c-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9765c-125">Requirements</span></span>  
 <span data-ttu-id="9765c-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9765c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9765c-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9765c-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9765c-128">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9765c-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9765c-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9765c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9765c-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9765c-130">See also</span></span>

- [<span data-ttu-id="9765c-131">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9765c-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="9765c-132">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9765c-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="9765c-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9765c-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9765c-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="9765c-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
