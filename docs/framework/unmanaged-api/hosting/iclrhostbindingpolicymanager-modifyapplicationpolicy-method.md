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
ms.openlocfilehash: e32714bba2403752f1ac2551ab182f2655f1fa75
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703857"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="a3996-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="a3996-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="a3996-103">Modyfikuje zasady powiązań dla określonego zestawu i tworzy nową wersję zasad.</span><span class="sxs-lookup"><span data-stu-id="a3996-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3996-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3996-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a3996-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3996-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="a3996-106">podczas Tożsamość zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="a3996-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="a3996-107">podczas Nowa tożsamość zmodyfikowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3996-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="a3996-108">podczas Wskaźnik do buforu, który zawiera dane zasad powiązań dla zestawu do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="a3996-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="a3996-109">podczas Rozmiar zasad powiązania, które mają zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="a3996-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="a3996-110">podczas Logiczne lub kombinacja wartości [EHostBindingPolicyModifyFlags —](ehostbindingpolicymodifyflags-enumeration.md) wskazujących na kontrolę przekierowania.</span><span class="sxs-lookup"><span data-stu-id="a3996-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="a3996-111">określoną Wskaźnik do buforu, który zawiera nowe dane zasad powiązań.</span><span class="sxs-lookup"><span data-stu-id="a3996-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="a3996-112">[in. out] Wskaźnik do rozmiaru nowego buforu zasad powiązania.</span><span class="sxs-lookup"><span data-stu-id="a3996-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3996-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3996-113">Return Value</span></span>  
  
|<span data-ttu-id="a3996-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3996-114">HRESULT</span></span>|<span data-ttu-id="a3996-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a3996-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3996-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3996-116">S_OK</span></span>|<span data-ttu-id="a3996-117">Zasady zostały zmodyfikowane pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a3996-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="a3996-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a3996-118">E_INVALIDARG</span></span>|<span data-ttu-id="a3996-119">`pwzSourceAssemblyIdentity`lub `pwzTargetAssemblyIdentity` było odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="a3996-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="a3996-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a3996-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a3996-121">`pbNewApplicationPolicy`jest za mała.</span><span class="sxs-lookup"><span data-stu-id="a3996-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="a3996-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3996-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3996-123">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a3996-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a3996-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a3996-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a3996-125">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="a3996-125">The call timed out.</span></span>|  
|<span data-ttu-id="a3996-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a3996-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a3996-127">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="a3996-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a3996-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a3996-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a3996-129">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="a3996-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a3996-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3996-130">E_FAIL</span></span>|<span data-ttu-id="a3996-131">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="a3996-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a3996-132">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="a3996-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a3996-133">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a3996-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3996-134">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3996-134">Remarks</span></span>  
 <span data-ttu-id="a3996-135">`ModifyApplicationPolicy`Metodę można wywołać dwukrotnie.</span><span class="sxs-lookup"><span data-stu-id="a3996-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="a3996-136">Pierwsze wywołanie powinno podawać wartość null dla `pbNewApplicationPolicy` parametru.</span><span class="sxs-lookup"><span data-stu-id="a3996-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="a3996-137">To wywołanie zwróci wartość wymaganą dla parametru `pcbNewAppPolicySize` .</span><span class="sxs-lookup"><span data-stu-id="a3996-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="a3996-138">Drugie wywołanie powinno dostarczyć tę wartość dla `pcbNewAppPolicySize` i wskazać bufor tego rozmiaru dla `pbNewApplicationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="a3996-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3996-139">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3996-139">Requirements</span></span>  
 <span data-ttu-id="a3996-140">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3996-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3996-141">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a3996-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3996-142">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3996-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3996-143">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3996-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3996-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3996-144">See also</span></span>

- [<span data-ttu-id="a3996-145">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3996-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
