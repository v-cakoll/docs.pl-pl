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
ms.openlocfilehash: d5323538447e083a0c727e43261dd68337182b9b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141077"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="66aa4-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="66aa4-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="66aa4-103">Modyfikuje zasady powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="66aa4-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66aa4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66aa4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="66aa4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66aa4-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="66aa4-106">podczas Tożsamość zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="66aa4-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="66aa4-107">podczas Nowa tożsamość zmodyfikowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="66aa4-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="66aa4-108">podczas Wskaźnik do buforu, który zawiera dane zasad powiązań dla zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="66aa4-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="66aa4-109">podczas Rozmiar zasad powiązania, które mają zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="66aa4-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="66aa4-110">podczas Logiczne lub kombinacja wartości [EHostBindingPolicyModifyFlags —](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wskazujących na kontrolę przekierowania.</span><span class="sxs-lookup"><span data-stu-id="66aa4-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="66aa4-111">określoną Wskaźnik do buforu, który zawiera nowe dane zasad powiązań.</span><span class="sxs-lookup"><span data-stu-id="66aa4-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="66aa4-112">[in. out] Wskaźnik do rozmiaru nowego buforu zasad powiązania.</span><span class="sxs-lookup"><span data-stu-id="66aa4-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66aa4-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="66aa4-113">Return Value</span></span>  
  
|<span data-ttu-id="66aa4-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="66aa4-114">HRESULT</span></span>|<span data-ttu-id="66aa4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="66aa4-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="66aa4-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="66aa4-116">S_OK</span></span>|<span data-ttu-id="66aa4-117">Zasady zostały zmodyfikowane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="66aa4-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="66aa4-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="66aa4-118">E_INVALIDARG</span></span>|<span data-ttu-id="66aa4-119">`pwzSourceAssemblyIdentity` lub `pwzTargetAssemblyIdentity` było odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="66aa4-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="66aa4-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="66aa4-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="66aa4-121">`pbNewApplicationPolicy` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="66aa4-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="66aa4-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="66aa4-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="66aa4-123">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="66aa4-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="66aa4-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="66aa4-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="66aa4-125">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="66aa4-125">The call timed out.</span></span>|  
|<span data-ttu-id="66aa4-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="66aa4-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="66aa4-127">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="66aa4-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="66aa4-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="66aa4-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="66aa4-129">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="66aa4-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="66aa4-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="66aa4-130">E_FAIL</span></span>|<span data-ttu-id="66aa4-131">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="66aa4-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="66aa4-132">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="66aa4-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="66aa4-133">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="66aa4-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66aa4-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66aa4-134">Remarks</span></span>  
 <span data-ttu-id="66aa4-135">Metodę `ModifyApplicationPolicy` można wywołać dwa razy.</span><span class="sxs-lookup"><span data-stu-id="66aa4-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="66aa4-136">Pierwsze wywołanie powinno podawać wartość null dla parametru `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="66aa4-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="66aa4-137">To wywołanie zwróci wartość wymaganą dla `pcbNewAppPolicySize`.</span><span class="sxs-lookup"><span data-stu-id="66aa4-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="66aa4-138">Drugie wywołanie powinno dostarczyć tę wartość dla `pcbNewAppPolicySize`i wskazać bufor tego rozmiaru dla `pbNewApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="66aa4-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66aa4-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66aa4-139">Requirements</span></span>  
 <span data-ttu-id="66aa4-140">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66aa4-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66aa4-141">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="66aa4-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66aa4-142">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="66aa4-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66aa4-143">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66aa4-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66aa4-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66aa4-144">See also</span></span>

- [<span data-ttu-id="66aa4-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="66aa4-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
