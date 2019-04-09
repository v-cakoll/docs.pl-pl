---
title: ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e926fb2753367370e9aca726806eb8747e32048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153741"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a>ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference — Metoda
Pobiera [iclrprobingassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw z typem określonej tożsamości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwMachineType`  
 [in] Prawidłowa wartość, która określa z architekturą procesora, zgodnie z definicją w pliku WinNT.h.  
  
 `dwFlags`  
 [in] Podana dla przyszłej rozszerzalności. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).  
  
 `pwzReferenceIdentity`  
 [in] Nieprzezroczysty powiązanie tożsamości, zwykle zwrócony z wywołania do [iclrassemblyidentitymanager::getbindingidentityfromfile —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) lub [iclrassemblyidentitymanager::getbindingidentityfromstream —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) metody.  
  
 `ppProbingAssemblyEnum`  
 [out] Wskaźnik interfejsu do `ICLRProbingAssemblyEnum` moduł wyliczający, który zawiera odwołania do zestawów odwołuje się zestaw identyfikowane przez `pwzReferenceIdentity`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda zwróciła pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
