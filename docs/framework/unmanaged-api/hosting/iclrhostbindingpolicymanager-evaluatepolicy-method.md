---
title: ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.EvaluatePolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::EvaluatePolicy method [.NET Framework hosting]
- EvaluatePolicy method [.NET Framework hosting]
ms.assetid: 3a3a9446-7a4e-4836-9b27-5c536c15993d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d23b2371e7cc3c9d1e91af061c19b4fb0dbc69e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779696"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="8095b-102">ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="8095b-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="8095b-103">Ocenia zasady tworzenia powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="8095b-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8095b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8095b-104">Syntax</span></span>  
  
```cpp  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8095b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8095b-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="8095b-106">[in] Odwołanie do zestawu przed oceny zasad.</span><span class="sxs-lookup"><span data-stu-id="8095b-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="8095b-107">[in] Wskaźnik do buforu, który zawiera dane zasad.</span><span class="sxs-lookup"><span data-stu-id="8095b-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="8095b-108">[in] Rozmiar `pbApplicationPolicy` buforu.</span><span class="sxs-lookup"><span data-stu-id="8095b-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="8095b-109">[out] Odwołanie do zestawu, po dokonaniu oceny nowe dane zasad.</span><span class="sxs-lookup"><span data-stu-id="8095b-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="8095b-110">[out w] Wskaźnik do rozmiar buforu odwołanie do zestawu tożsamości, po dokonaniu oceny nowe dane zasad.</span><span class="sxs-lookup"><span data-stu-id="8095b-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="8095b-111">[out] Wskaźnik do logicznego lub kombinacji [ebindpolicylevels —](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) wartości, wskazując, które zasady zostały zastosowane.</span><span class="sxs-lookup"><span data-stu-id="8095b-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8095b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8095b-112">Return Value</span></span>  
  
|<span data-ttu-id="8095b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8095b-113">HRESULT</span></span>|<span data-ttu-id="8095b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8095b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8095b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8095b-115">S_OK</span></span>|<span data-ttu-id="8095b-116">Ocena została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8095b-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="8095b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8095b-117">E_INVALIDARG</span></span>|<span data-ttu-id="8095b-118">Albo `pwzReferenceIdentity` lub `pbApplicationPolicy` jest odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="8095b-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="8095b-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8095b-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8095b-120">`cbAppPolicySize` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="8095b-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="8095b-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8095b-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8095b-122">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="8095b-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8095b-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8095b-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8095b-124">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="8095b-124">The call timed out.</span></span>|  
|<span data-ttu-id="8095b-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8095b-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8095b-126">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="8095b-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8095b-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8095b-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8095b-128">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="8095b-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8095b-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8095b-129">E_FAIL</span></span>|<span data-ttu-id="8095b-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="8095b-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8095b-131">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8095b-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8095b-132">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8095b-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8095b-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8095b-133">Remarks</span></span>  
 <span data-ttu-id="8095b-134">`EvaluatePolicy` Metoda umożliwia hosta do wywierania wpływu na politykę powiązania do zachowania specyficzne dla hosta zestawu wymagań dotyczących przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="8095b-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="8095b-135">Aparat zasad, sama pozostaje wewnątrz środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8095b-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8095b-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8095b-136">Requirements</span></span>  
 <span data-ttu-id="8095b-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8095b-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8095b-138">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8095b-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8095b-139">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8095b-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8095b-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8095b-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8095b-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8095b-141">See also</span></span>

- [<span data-ttu-id="8095b-142">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8095b-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
