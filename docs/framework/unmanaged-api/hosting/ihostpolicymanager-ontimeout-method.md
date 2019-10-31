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
ms.openlocfilehash: e8a14dd6a6d196cea9caa6be669b2b75a167eca8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141104"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="a8c0b-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8c0b-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="a8c0b-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma wykonać akcję określoną przez wywołanie metody [ICLRPolicyManager:: SetActionOnTimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c0b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8c0b-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8c0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8c0b-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="a8c0b-106">podczas Jedna z wartości [EClrOperation —](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) , wskazująca rodzaj operacji, która przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="a8c0b-107">podczas Jedna z wartości [EPolicyAction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) , wskazująca na akcję, którą wykonuje środowisko CLR w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8c0b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a8c0b-108">Return Value</span></span>  
  
|<span data-ttu-id="a8c0b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8c0b-109">HRESULT</span></span>|<span data-ttu-id="a8c0b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a8c0b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8c0b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8c0b-111">S_OK</span></span>|<span data-ttu-id="a8c0b-112">`OnTimeout` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="a8c0b-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a8c0b-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a8c0b-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a8c0b-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a8c0b-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a8c0b-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-116">The call timed out.</span></span>|  
|<span data-ttu-id="a8c0b-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a8c0b-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a8c0b-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a8c0b-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a8c0b-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a8c0b-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a8c0b-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a8c0b-121">E_FAIL</span></span>|<span data-ttu-id="a8c0b-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a8c0b-123">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a8c0b-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a8c0b-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8c0b-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8c0b-125">Requirements</span></span>  
 <span data-ttu-id="a8c0b-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8c0b-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8c0b-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8c0b-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8c0b-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8c0b-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8c0b-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8c0b-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c0b-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8c0b-130">See also</span></span>

- [<span data-ttu-id="a8c0b-131">EClrOperation, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a8c0b-131">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="a8c0b-132">EPolicyAction, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a8c0b-132">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="a8c0b-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8c0b-133">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="a8c0b-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8c0b-134">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
