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
ms.openlocfilehash: 9600573a0a730cee10247d5644d587e75856cdd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141178"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="ad0c4-102">ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad0c4-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="ad0c4-103">Oblicza zasady powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad0c4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad0c4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ad0c4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad0c4-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="ad0c4-106">podczas Odwołanie do zestawu przed oceną zasad.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="ad0c4-107">podczas Wskaźnik do buforu, który zawiera dane zasad.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="ad0c4-108">podczas Rozmiar buforu `pbApplicationPolicy`.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="ad0c4-109">określoną Odwołanie do zestawu po dokonaniu oceny nowych danych zasad.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="ad0c4-110">[in. out] Wskaźnik do rozmiaru buforu odwołań tożsamości zestawu po dokonaniu oceny nowych danych zasad.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="ad0c4-111">określoną Wskaźnik do logicznej lub kombinacji wartości [EBindPolicyLevels —](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) wskazujących, które zasady zostały zastosowane.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad0c4-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ad0c4-112">Return Value</span></span>  
  
|<span data-ttu-id="ad0c4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad0c4-113">HRESULT</span></span>|<span data-ttu-id="ad0c4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ad0c4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad0c4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad0c4-115">S_OK</span></span>|<span data-ttu-id="ad0c4-116">Ocena została zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="ad0c4-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad0c4-117">E_INVALIDARG</span></span>|<span data-ttu-id="ad0c4-118">`pwzReferenceIdentity` lub `pbApplicationPolicy` jest odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="ad0c4-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ad0c4-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ad0c4-120">`cbAppPolicySize` jest za mały.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="ad0c4-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad0c4-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad0c4-122">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad0c4-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad0c4-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad0c4-124">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-124">The call timed out.</span></span>|  
|<span data-ttu-id="ad0c4-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad0c4-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad0c4-126">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad0c4-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad0c4-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad0c4-128">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad0c4-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad0c4-129">E_FAIL</span></span>|<span data-ttu-id="ad0c4-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad0c4-131">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad0c4-132">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad0c4-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad0c4-133">Remarks</span></span>  
 <span data-ttu-id="ad0c4-134">Metoda `EvaluatePolicy` umożliwia hostowi wpływ na powiązania zasad w celu obsługi wymagań dotyczących wersji zestawu specyficznych dla hosta.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="ad0c4-135">Sam aparat zasad pozostaje wewnątrz środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="ad0c4-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad0c4-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad0c4-136">Requirements</span></span>  
 <span data-ttu-id="ad0c4-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad0c4-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad0c4-138">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ad0c4-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad0c4-139">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad0c4-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad0c4-140">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad0c4-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0c4-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad0c4-141">See also</span></span>

- [<span data-ttu-id="ad0c4-142">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad0c4-142">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
