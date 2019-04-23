---
title: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream method [.NET Framework hosting]
- GetReferencedAssembliesFromStream method [.NET Framework hosting]
ms.assetid: fe9849c1-c3fc-477b-a31f-e8619f5516f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d6f93ee7870c9d81394ee55c5574c52c2aea50a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223124"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromstream-method"></a>ICLRAssemblyIdentityManager::GetReferencedAssembliesFromStream — Metoda
Pobiera wskaźnik do [iclrreferenceassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReferencedAssembliesFromStream (  
    [in]  IStream *pStream,  
    [in]  DWORD    dwFlags,  
    [in]  ICLRAssemblyReferenceList  *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik interfejsu do `IStream` zawierającego zestaw, który ma zostać obliczone.  
  
 `dwFlags`  
 [in] Podana dla przyszłej rozszerzalności. CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT stanowi jedyną wartość, która obsługuje bieżącą wersję środowiska uruchomieniowego języka wspólnego (CLR).  
  
 `pExcludeAssembliesList`  
 [in] Wskaźnik do [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) obiekt, który zawiera dane o tożsamości zestawu dla zestawów, które mają być wykluczone z `ppReferenceEnum`.  
  
 `ppReferenceEnum`  
 [out] Wskaźnik na adres `ICLRReferenceAssemblyEnum` obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w `pStream`, z wyłączeniem zestawów w `pExcludeAssembliesList`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda zwróciła pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt wywołujący, można wykluczyć zestaw odwołania do zestawu znanych z liście zwracanych. Ten zestaw jest definiowany przez `pExcludeAssembliesList`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRReferenceAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)
