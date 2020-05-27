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
ms.openlocfilehash: fb0f943d710322257d052edc5c16108671622790
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804219"
---
# <a name="ihostpolicymanagerontimeout-method"></a><span data-ttu-id="8c3f9-102">IHostPolicyManager::OnTimeout — Metoda</span><span class="sxs-lookup"><span data-stu-id="8c3f9-102">IHostPolicyManager::OnTimeout Method</span></span>
<span data-ttu-id="8c3f9-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma wykonać akcję określoną przez wywołanie metody [ICLRPolicyManager:: SetActionOnTimeout —](iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) method in response to a timeout.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c3f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c3f9-104">Syntax</span></span>  
  
```cpp  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c3f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8c3f9-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="8c3f9-106">podczas Jedna z wartości [EClrOperation —](eclroperation-enumeration.md) , wskazująca rodzaj operacji, która przekroczyła limit czasu.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the kind of operation that timed out.</span></span>  
  
 `action`  
 <span data-ttu-id="8c3f9-107">podczas Jedna z wartości [EPolicyAction —](epolicyaction-enumeration.md) , wskazująca na akcję, którą wykonuje środowisko CLR w odpowiedzi na limit czasu.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to the timeout.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c3f9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8c3f9-108">Return Value</span></span>  
  
|<span data-ttu-id="8c3f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c3f9-109">HRESULT</span></span>|<span data-ttu-id="8c3f9-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8c3f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c3f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c3f9-111">S_OK</span></span>|<span data-ttu-id="8c3f9-112">`OnTimeout`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-112">`OnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="8c3f9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c3f9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c3f9-114">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c3f9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c3f9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c3f9-116">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-116">The call timed out.</span></span>|  
|<span data-ttu-id="8c3f9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c3f9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c3f9-118">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c3f9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c3f9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c3f9-120">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c3f9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c3f9-121">E_FAIL</span></span>|<span data-ttu-id="8c3f9-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c3f9-123">Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c3f9-124">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8c3f9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c3f9-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c3f9-125">Requirements</span></span>  
 <span data-ttu-id="8c3f9-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c3f9-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c3f9-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c3f9-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c3f9-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c3f9-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c3f9-129">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c3f9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3f9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c3f9-130">See also</span></span>

- [<span data-ttu-id="8c3f9-131">EClrOperation — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8c3f9-131">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="8c3f9-132">EPolicyAction — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8c3f9-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="8c3f9-133">ICLRPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c3f9-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="8c3f9-134">IHostPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c3f9-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
