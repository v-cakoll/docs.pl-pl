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
# <a name="iclrhostbindingpolicymanagerevaluatepolicy-method"></a>ICLRHostBindingPolicyManager::EvaluatePolicy — Metoda
Oblicza zasady powiązań w imieniu hosta.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parameters"></a>Parametry  
 `pwzReferenceIdentity`  
 podczas Odwołanie do zestawu przed oceną zasad.  
  
 `pbApplicationPolicy`  
 podczas Wskaźnik do buforu, który zawiera dane zasad.  
  
 `cbAppPolicySize`  
 podczas Rozmiar buforu `pbApplicationPolicy`.  
  
 `pwzPostPolicyReferenceIdentity`  
 określoną Odwołanie do zestawu po dokonaniu oceny nowych danych zasad.  
  
 `pcchPostPolicyReferenceIdentity`  
 [in. out] Wskaźnik do rozmiaru buforu odwołań tożsamości zestawu po dokonaniu oceny nowych danych zasad.  
  
 `pdwPoliciesApplied`  
 określoną Wskaźnik do logicznej lub kombinacji wartości [EBindPolicyLevels —](../../../../docs/framework/unmanaged-api/hosting/ebindpolicylevels-enumeration.md) wskazujących, które zasady zostały zastosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Ocena została zakończona pomyślnie.|  
|E_INVALIDARG|`pwzReferenceIdentity` lub `pbApplicationPolicy` jest odwołaniem o wartości null.|  
|ERROR_INSUFFICIENT_BUFFER|`cbAppPolicySize` jest za mały.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `EvaluatePolicy` umożliwia hostowi wpływ na powiązania zasad w celu obsługi wymagań dotyczących wersji zestawu specyficznych dla hosta. Sam aparat zasad pozostaje wewnątrz środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
