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
ms.openlocfilehash: f72a66354bfc907dab7ebc24de515bdfb20ddfb2
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703593"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a><span data-ttu-id="94564-102">ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="94564-102">ICLRHostBindingPolicyManager::EvaluatePolicy Method</span></span>
<span data-ttu-id="94564-103">Oblicza zasady powiązań w imieniu hosta.</span><span class="sxs-lookup"><span data-stu-id="94564-103">Evaluates binding policy on behalf of the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94564-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94564-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="94564-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94564-105">Parameters</span></span>  
 `pwzReferenceIdentity`  
 <span data-ttu-id="94564-106">podczas Odwołanie do zestawu przed oceną zasad.</span><span class="sxs-lookup"><span data-stu-id="94564-106">[in] A reference to the assembly before the policy evaluation.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="94564-107">podczas Wskaźnik do buforu, który zawiera dane zasad.</span><span class="sxs-lookup"><span data-stu-id="94564-107">[in] A pointer to a buffer that contains the policy data.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="94564-108">podczas Rozmiar `pbApplicationPolicy` buforu.</span><span class="sxs-lookup"><span data-stu-id="94564-108">[in] The size of the `pbApplicationPolicy` buffer.</span></span>  
  
 `pwzPostPolicyReferenceIdentity`  
 <span data-ttu-id="94564-109">określoną Odwołanie do zestawu po dokonaniu oceny nowych danych zasad.</span><span class="sxs-lookup"><span data-stu-id="94564-109">[out] A reference to the assembly after the evaluation of the new policy data.</span></span>  
  
 `pcchPostPolicyReferenceIdentity`  
 <span data-ttu-id="94564-110">[in. out] Wskaźnik do rozmiaru buforu odwołań tożsamości zestawu po dokonaniu oceny nowych danych zasad.</span><span class="sxs-lookup"><span data-stu-id="94564-110">[in, out] A pointer to the size of the assembly identity reference buffer after the evaluation of the new policy data.</span></span>  
  
 `pdwPoliciesApplied`  
 <span data-ttu-id="94564-111">określoną Wskaźnik do logicznej lub kombinacji wartości [EBindPolicyLevels —](ebindpolicylevels-enumeration.md) wskazujących, które zasady zostały zastosowane.</span><span class="sxs-lookup"><span data-stu-id="94564-111">[out] A pointer to a logical OR combination of [EBindPolicyLevels](ebindpolicylevels-enumeration.md) values, indicating which policies have been applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94564-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94564-112">Return Value</span></span>  
  
|<span data-ttu-id="94564-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94564-113">HRESULT</span></span>|<span data-ttu-id="94564-114">Opis</span><span class="sxs-lookup"><span data-stu-id="94564-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94564-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="94564-115">S_OK</span></span>|<span data-ttu-id="94564-116">Ocena została zakończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="94564-116">The evaluation completed successfully.</span></span>|  
|<span data-ttu-id="94564-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="94564-117">E_INVALIDARG</span></span>|<span data-ttu-id="94564-118">Albo `pwzReferenceIdentity` `pbApplicationPolicy` jest odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="94564-118">Either `pwzReferenceIdentity` or `pbApplicationPolicy` is a null reference.</span></span>|  
|<span data-ttu-id="94564-119">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="94564-119">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="94564-120">`cbAppPolicySize`jest za mała.</span><span class="sxs-lookup"><span data-stu-id="94564-120">`cbAppPolicySize` is too small.</span></span>|  
|<span data-ttu-id="94564-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94564-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94564-122">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="94564-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94564-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94564-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94564-124">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="94564-124">The call timed out.</span></span>|  
|<span data-ttu-id="94564-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94564-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94564-126">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="94564-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94564-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94564-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94564-128">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="94564-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94564-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94564-129">E_FAIL</span></span>|<span data-ttu-id="94564-130">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="94564-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94564-131">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="94564-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94564-132">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="94564-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94564-133">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94564-133">Remarks</span></span>  
 <span data-ttu-id="94564-134">`EvaluatePolicy`Metoda umożliwia hostowi wpływ na powiązania zasad w celu obsługi wymagań dotyczących wersji zestawu specyficznych dla hosta.</span><span class="sxs-lookup"><span data-stu-id="94564-134">The `EvaluatePolicy` method allows the host to influence binding policy to maintain host-specific assembly versioning requirements.</span></span> <span data-ttu-id="94564-135">Sam aparat zasad pozostaje wewnątrz środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="94564-135">The policy engine itself remains inside the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94564-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94564-136">Requirements</span></span>  
 <span data-ttu-id="94564-137">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94564-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94564-138">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="94564-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94564-139">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="94564-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94564-140">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94564-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94564-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94564-141">See also</span></span>

- [<span data-ttu-id="94564-142">ICLRHostBindingPolicyManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="94564-142">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
