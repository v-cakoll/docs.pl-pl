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
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda
Modyfikuje zasad tworzenia powiązań dla określonego zestawu i tworzy nową wersję zasad.  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="parameters"></a>Parametry  
 `pwzSourceAssemblyIdentity`  
 [in] Tożsamość zestawu do modyfikacji.  
  
 `pwzTargetAssemblyIdentity`  
 [in] Nową tożsamość zestawu zmodyfikowane.  
  
 `pbApplicationPolicy`  
 [in] Wskaźnik do buforu, który zawiera dane zasad powiązania dla zestawu do modyfikacji.  
  
 `cbAppPolicySize`  
 [in] Rozmiar zasad powiązanie ma zostać zastąpione.  
  
 `dwPolicyModifyFlags`  
 [in] Logiczne OR kombinacji [ehostbindingpolicymodifyflags —](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wartości, wskazując kontroli przekierowania.  
  
 `pbNewApplicationPolicy`  
 [out] Wskaźnik do buforu, który zawiera nowe powiązanie danych zasad.  
  
 `pcbNewAppPolicySize`  
 [out w] Wskaźnik do rozmiar buforu do zasad nowego powiązania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Pomyślnie modyfikacji zasad.|  
|E_INVALIDARG|`pwzSourceAssemblyIdentity` lub `pwzTargetAssemblyIdentity` został odwołanie o wartości null.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy` jest za mały.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ModifyApplicationPolicy` Metoda może być wywoływana dwa razy. Pierwsze wywołanie należy podać wartość null dla `pbNewApplicationPolicy` parametru. To wywołanie spowoduje zwrócenie o wartości niezbędne `pcbNewAppPolicySize`. Drugie wywołanie należy podać tę wartość dla `pcbNewAppPolicySize`, a następnie wskaż buforu tego rozmiaru dla `pbNewApplicationPolicy`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
