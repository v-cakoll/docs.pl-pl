---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07a4998f86958e21fffc8ba8657ec9f2a170f43e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112440"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="ad85d-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad85d-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="ad85d-103">Modyfikuje zasad tworzenia powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="ad85d-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad85d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad85d-104">Syntax</span></span>  
  
```  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,   
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,   
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad85d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad85d-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="ad85d-106">[in] Tożsamość zestawu do modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ad85d-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="ad85d-107">[in] Nową tożsamość zestawu zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="ad85d-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="ad85d-108">[in] Wskaźnik do buforu, który zawiera dane zasad powiązania dla zestawu do modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="ad85d-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="ad85d-109">[in] Rozmiar zasad powiązanie ma zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="ad85d-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="ad85d-110">[in] Logiczne OR kombinacji [ehostbindingpolicymodifyflags —](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wartości, wskazując kontroli przekierowania.</span><span class="sxs-lookup"><span data-stu-id="ad85d-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="ad85d-111">[out] Wskaźnik do buforu, który zawiera nowe powiązanie danych zasad.</span><span class="sxs-lookup"><span data-stu-id="ad85d-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="ad85d-112">[out w] Wskaźnik do rozmiar buforu do zasad nowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ad85d-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad85d-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad85d-113">Return Value</span></span>  
  
|<span data-ttu-id="ad85d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad85d-114">HRESULT</span></span>|<span data-ttu-id="ad85d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="ad85d-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad85d-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad85d-116">S_OK</span></span>|<span data-ttu-id="ad85d-117">Pomyślnie modyfikacji zasad.</span><span class="sxs-lookup"><span data-stu-id="ad85d-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="ad85d-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad85d-118">E_INVALIDARG</span></span>|<span data-ttu-id="ad85d-119">`pwzSourceAssemblyIdentity` lub `pwzTargetAssemblyIdentity` został odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ad85d-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="ad85d-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ad85d-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ad85d-121">`pbNewApplicationPolicy` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="ad85d-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="ad85d-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad85d-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad85d-123">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="ad85d-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad85d-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad85d-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad85d-125">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="ad85d-125">The call timed out.</span></span>|  
|<span data-ttu-id="ad85d-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad85d-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad85d-127">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="ad85d-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad85d-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad85d-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad85d-129">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="ad85d-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad85d-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad85d-130">E_FAIL</span></span>|<span data-ttu-id="ad85d-131">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ad85d-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad85d-132">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="ad85d-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad85d-133">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ad85d-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad85d-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad85d-134">Remarks</span></span>  
 <span data-ttu-id="ad85d-135">`ModifyApplicationPolicy` Metoda może być wywoływana dwa razy.</span><span class="sxs-lookup"><span data-stu-id="ad85d-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="ad85d-136">Pierwsze wywołanie należy podać wartość null dla `pbNewApplicationPolicy` parametru.</span><span class="sxs-lookup"><span data-stu-id="ad85d-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="ad85d-137">To wywołanie spowoduje zwrócenie o wartości niezbędne `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="ad85d-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="ad85d-138">Drugie wywołanie należy podać tę wartość dla `pcbNewAppPolicySize`, a następnie wskaż buforu tego rozmiaru dla `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="ad85d-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad85d-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad85d-139">Requirements</span></span>  
 <span data-ttu-id="ad85d-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad85d-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad85d-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad85d-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad85d-142">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad85d-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad85d-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad85d-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad85d-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad85d-144">See also</span></span>

- [<span data-ttu-id="ad85d-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad85d-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
