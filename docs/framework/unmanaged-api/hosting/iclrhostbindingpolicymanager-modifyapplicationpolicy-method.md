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
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda
Modyfikuje zasady powiązań dla określonego zestawu i tworzy nową wersję zasad.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parameters"></a>Parametry  
 `pwzSourceAssemblyIdentity`  
 podczas Tożsamość zestawu do zmodyfikowania.  
  
 `pwzTargetAssemblyIdentity`  
 podczas Nowa tożsamość zmodyfikowanego zestawu.  
  
 `pbApplicationPolicy`  
 podczas Wskaźnik do buforu, który zawiera dane zasad powiązań dla zestawu do zmodyfikowania.  
  
 `cbAppPolicySize`  
 podczas Rozmiar zasad powiązania, które mają zostać zastąpione.  
  
 `dwPolicyModifyFlags`  
 podczas Logiczne lub kombinacja wartości [EHostBindingPolicyModifyFlags —](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wskazujących na kontrolę przekierowania.  
  
 `pbNewApplicationPolicy`  
 określoną Wskaźnik do buforu, który zawiera nowe dane zasad powiązań.  
  
 `pcbNewAppPolicySize`  
 [in. out] Wskaźnik do rozmiaru nowego buforu zasad powiązania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Zasady zostały zmodyfikowane pomyślnie.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` lub `pwzTargetAssemblyIdentity` było odwołaniem o wartości null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` jest za mały.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Metodę `ModifyApplicationPolicy` można wywołać dwa razy. Pierwsze wywołanie powinno podawać wartość null dla parametru `pbNewApplicationPolicy`. To wywołanie zwróci wartość wymaganą dla `pcbNewAppPolicySize`. Drugie wywołanie powinno dostarczyć tę wartość dla `pcbNewAppPolicySize`i wskazać bufor tego rozmiaru dla `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
