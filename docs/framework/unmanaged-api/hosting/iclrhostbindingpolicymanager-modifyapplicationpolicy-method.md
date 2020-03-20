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
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a>ICLRHostBindingPolicyManager::ModifyApplicationPolicy — Metoda
Modyfikuje zasady wiązania dla określonego zestawu i tworzy nową wersję zasad.  
  
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
 [w] Tożsamość zestawu do zmodyfikowania.  
  
 `pwzTargetAssemblyIdentity`  
 [w] Nowa tożsamość zmodyfikowanego zestawu.  
  
 `pbApplicationPolicy`  
 [w] Wskaźnik do buforu, który zawiera dane zasad wiązania dla zestawu do zmodyfikowania.  
  
 `cbAppPolicySize`  
 [w] Rozmiar zasad wiązania, które mają zostać zastąpione.  
  
 `dwPolicyModifyFlags`  
 [w] Logiczna kombinacja OR [wartości EHostBindingPolicyModifyFlags,](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) wskazująca kontrolę nad przekierowaniem.  
  
 `pbNewApplicationPolicy`  
 [na zewnątrz] Wskaźnik do buforu, który zawiera nowe dane zasad wiązania.  
  
 `pcbNewAppPolicySize`  
 [w, na zewnątrz] Wskaźnik do rozmiaru nowego buforu zasad wiązania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Zasady zostały pomyślnie zmodyfikowane.|  
|E_invalidarg|`pwzSourceAssemblyIdentity`lub `pwzTargetAssemblyIdentity` był odwołaniem zerowym.|  
|ERROR_INSUFFICIENT_BUFFER|`pbNewApplicationPolicy`jest zbyt mała.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.|  
|E_fail|Doszło do nieznanej katastrofalnej awarii. Po metoda zwraca E_FAIL, CLR nie jest już użyteczny w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Metodę `ModifyApplicationPolicy` można wywołać dwa razy. Pierwsze wywołanie powinno podać wartość `pbNewApplicationPolicy` null dla parametru. To wywołanie powróci z `pcbNewAppPolicySize`niezbędną wartością dla . Drugie wywołanie powinno podać `pcbNewAppPolicySize`tę wartość dla i wskazać `pbNewApplicationPolicy`bufor o tym rozmiarze dla .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
