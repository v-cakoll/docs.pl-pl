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
ms.openlocfilehash: ad7856a9376880f867e35f1e63bc2cac1ca216fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130158"
---
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda
Ocenia zasady tworzenia powiązań w imieniu hosta.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EvaluatePolicy (  
    [in] LPCWSTR     pwzReferenceIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [out, size_is(*pcchPostPolicyReferenceIdentity)] LPWSTR pwzPostPolicyReferenceIdentity,  
    [in, out] DWORD *pcchPostPolicyReferenceIdentity,  
    [out] DWORD     *pdwPoliciesApplied  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzReferenceIdentity`  
 [in] Odwołanie do zestawu przed oceny zasad.  
  
 `pbApplicationPolicy`  
 [in] Wskaźnik do buforu, który zawiera dane zasad.  
  
 `cbAppPolicySize`  
 [in] Rozmiar `pbApplicationPolicy` buforu.  
  
 `pwzPostPolicyReferenceIdentity`  
 [out] Odwołanie do zestawu, po dokonaniu oceny nowe dane zasad.  
  
 `pcchPostPolicyReferenceIdentity`  
 [out w] Wskaźnik do rozmiar buforu odwołanie do zestawu tożsamości, po dokonaniu oceny nowe dane zasad.  
  
 `pdwPoliciesApplied`  
 [out] Wskaźnik do logicznego lub kombinacji [ebindpolicylevels —](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) wartości, wskazując, które zasady zostały zastosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Ocena została ukończona pomyślnie.|  
|E_INVALIDARG|Albo `pwzReferenceIdentity` lub `pbApplicationPolicy` jest odwołanie o wartości null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` jest za mały.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `EvaluatePolicy` Metoda umożliwia hosta do wywierania wpływu na politykę powiązania do zachowania specyficzne dla hosta zestawu wymagań dotyczących przechowywania wersji. Aparat zasad, sama pozostaje wewnątrz środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
