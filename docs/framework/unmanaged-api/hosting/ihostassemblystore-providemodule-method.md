---
title: IHostAssemblyStore::ProvideModule — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9290fd70b17b5a6456d85cb4b037ebbc62e028f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763977"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule — Metoda
Usuwa plik zasobów modułu w zestawie lub połączone (ale nie embedded).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [in] Wskaźnik do [modulebindinfo —](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) wystąpienia, opisujący żądany moduł <xref:System.AppDomain>, zestawu i nazwa modułu.  
  
 `pdwModuleId`  
 [out] Wskaźnik do Unikatowy identyfikator `IStream` zawierający załadowanym module.  
  
 `ppStmModuleImage`  
 [out] Wskaźnik na adres `IStream` obiekt, który zawiera obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć modułu.  
  
 `ppStmPDB`  
 [out] Wskaźnik na adres `IStream` obiekt, który zawiera informacje o debugowaniu (PDB) program dla żądanego modułu, lub wartość null, jeśli nie można odnaleźć pliku .pdb.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideModule` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Nie można zlokalizować żądanego zestawu lub zasobu połączonego.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` nie jest wystarczająco duży, aby zawierała identyfikator, który chce hosta, aby zwrócić.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość tożsamości dla `pdwModuleId` określonej przez hosta. Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu. Środowisko CLR używa tej wartości jako unikatowy identyfikator dla skojarzonego strumienia. Sprawdza każdej wartości w odniesieniu do wartości dla `pAssemblyId` zwracane przez wywołania do [provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i przed wartości `pdwModuleId` zwracane przez inne wywołania do `ProvideModule`. Jeśli host zwraca taką samą wartość identyfikatora dla innego `IStream`, środowisko CLR sprawdza, czy zawartość strumieniu ma już zamapowana. Jeśli tak, środowisko CLR ładuje istniejącą kopię obrazu zamiast nowe mapowanie. W związku z tym, identyfikator także nie może nakładać o identyfikatorach zestawu zwróciło `ProvideAssembly`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
