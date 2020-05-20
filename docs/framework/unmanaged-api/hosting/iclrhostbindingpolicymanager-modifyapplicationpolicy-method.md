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
 podczas Logiczne lub kombinacja wartości [EHostBindingPolicyModifyFlags —](ehostbindingpolicymodifyflags-enumeration.md) wskazujących na kontrolę przekierowania.  
  
 `pbNewApplicationPolicy`  
 określoną Wskaźnik do buforu, który zawiera nowe dane zasad powiązań.  
  
 `pcbNewAppPolicySize`  
 [in. out] Wskaźnik do rozmiaru nowego buforu zasad powiązania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Zasady zostały zmodyfikowane pomyślnie.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity`lub `pwzTargetAssemblyIdentity` było odwołaniem o wartości null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`jest za mała.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ModifyApplicationPolicy`Metodę można wywołać dwukrotnie. Pierwsze wywołanie powinno podawać wartość null dla `pbNewApplicationPolicy` parametru. To wywołanie zwróci wartość wymaganą dla parametru `pcbNewAppPolicySize` . Drugie wywołanie powinno dostarczyć tę wartość dla `pcbNewAppPolicySize` i wskazać bufor tego rozmiaru dla `pbNewApplicationPolicy` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](iclrhostbindingpolicymanager-interface.md)
