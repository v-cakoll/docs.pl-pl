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
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178099"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="c4162-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="c4162-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="c4162-103">Modyfikuje zasady wiązania dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="c4162-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4162-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4162-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="c4162-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4162-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="c4162-106">[w] Tożsamość zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="c4162-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="c4162-107">[w] Nowa tożsamość zmodyfikowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c4162-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="c4162-108">[w] Wskaźnik do buforu, który zawiera dane zasad wiązania dla zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="c4162-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="c4162-109">[w] Rozmiar zasad wiązania, które mają zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="c4162-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="c4162-110">[w] Logiczna kombinacja OR [wartości EHostBindingPolicyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wskazująca kontrolę nad przekierowaniem.</span><span class="sxs-lookup"><span data-stu-id="c4162-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="c4162-111">[na zewnątrz] Wskaźnik do buforu, który zawiera nowe dane zasad wiązania.</span><span class="sxs-lookup"><span data-stu-id="c4162-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="c4162-112">[w, na zewnątrz] Wskaźnik do rozmiaru nowego buforu zasad wiązania.</span><span class="sxs-lookup"><span data-stu-id="c4162-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4162-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c4162-113">Return Value</span></span>  
  
|<span data-ttu-id="c4162-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4162-114">HRESULT</span></span>|<span data-ttu-id="c4162-115">Opis</span><span class="sxs-lookup"><span data-stu-id="c4162-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4162-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4162-116">S_OK</span></span>|<span data-ttu-id="c4162-117">Zasady zostały pomyślnie zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="c4162-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="c4162-118">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="c4162-118">E_INVALIDARG</span></span>|<span data-ttu-id="c4162-119">`pwzSourceAssemblyIdentity`lub `pwzTargetAssemblyIdentity` był odwołaniem zerowym.</span><span class="sxs-lookup"><span data-stu-id="c4162-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="c4162-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="c4162-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="c4162-121">`pbNewApplicationPolicy`jest zbyt mała.</span><span class="sxs-lookup"><span data-stu-id="c4162-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="c4162-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4162-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4162-123">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c4162-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4162-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4162-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4162-125">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="c4162-125">The call timed out.</span></span>|  
|<span data-ttu-id="c4162-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4162-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4162-127">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="c4162-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4162-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4162-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4162-129">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="c4162-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4162-130">E_fail</span><span class="sxs-lookup"><span data-stu-id="c4162-130">E_FAIL</span></span>|<span data-ttu-id="c4162-131">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="c4162-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4162-132">Po metoda zwraca E_FAIL, CLR nie jest już użyteczny w procesie.</span><span class="sxs-lookup"><span data-stu-id="c4162-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4162-133">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4162-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4162-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4162-134">Remarks</span></span>  
 <span data-ttu-id="c4162-135">Metodę `ModifyApplicationPolicy` można wywołać dwa razy.</span><span class="sxs-lookup"><span data-stu-id="c4162-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="c4162-136">Pierwsze wywołanie powinno podać wartość `pbNewApplicationPolicy` null dla parametru.</span><span class="sxs-lookup"><span data-stu-id="c4162-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="c4162-137">To wywołanie powróci z `pcbNewAppPolicySize`niezbędną wartością dla .</span><span class="sxs-lookup"><span data-stu-id="c4162-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="c4162-138">Drugie wywołanie powinno podać `pcbNewAppPolicySize`tę wartość dla i wskazać `pbNewApplicationPolicy`bufor o tym rozmiarze dla .</span><span class="sxs-lookup"><span data-stu-id="c4162-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4162-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4162-139">Requirements</span></span>  
 <span data-ttu-id="c4162-140">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4162-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4162-141">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4162-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4162-142">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4162-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4162-143">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4162-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4162-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4162-144">See also</span></span>

- [<span data-ttu-id="c4162-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="c4162-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
