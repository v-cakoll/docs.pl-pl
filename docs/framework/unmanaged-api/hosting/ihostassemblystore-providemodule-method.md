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
ms.openlocfilehash: eed09a8149a21140ad61133f29391f86cb0fb929
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124469"
---
# <a name="ihostassemblystoreprovidemodule-method"></a>IHostAssemblyStore::ProvideModule — Metoda
Rozpoznaje moduł wewnątrz zestawu lub połączony (ale nie osadzony) plik zasobów.  
  
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
 podczas Wskaźnik do wystąpienia [ModuleBindInfo —](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md) , który opisuje <xref:System.AppDomain>, zestaw i nazwę modułu żądanego modułu.  
  
 `pdwModuleId`  
 określoną Wskaźnik do unikatowego identyfikatora `IStream` zawierającego załadowany moduł.  
  
 `ppStmModuleImage`  
 określoną Wskaźnik do adresu obiektu `IStream`, który zawiera obraz przenośnego pliku wykonywalnego (PE), który ma zostać załadowany lub ma wartość null, jeśli nie można znaleźć modułu.  
  
 `ppStmPDB`  
 określoną Wskaźnik na adres `IStream` obiektu, który zawiera informacje o debugowaniu programu (PDB) dla żądanego modułu, lub wartość null, jeśli nie można znaleźć pliku. pdb.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideModule` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Nie można zlokalizować żądanego zestawu lub połączonego zasobu.|  
|E_NOT_SUFFICIENT_BUFFER|`pdwModuleId` nie jest wystarczająco duży, aby można było zawierać identyfikator, który chce zwrócić host.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość tożsamości zwrócona dla `pdwModuleId` jest określona przez hosta. Identyfikatory muszą być unikatowe w okresie istnienia procesu. Środowisko CLR używa tej wartości jako unikatowego identyfikatora skojarzonego strumienia. Sprawdza każdą wartość w odniesieniu do wartości `pAssemblyId` zwracanych przez wywołania do [ProvideAssembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) i wartości dla `pdwModuleId` zwracanych przez inne wywołania do `ProvideModule`. Jeśli host zwraca tę samą wartość identyfikatora dla innego `IStream`, środowisko CLR sprawdzi, czy zawartość tego strumienia została już zamapowana. Jeśli tak, środowisko CLR ładuje istniejącą kopię obrazu zamiast mapowania nowej. W związku z tym, identyfikator nie może również nakładać się na identyfikatory zestawu zwrócone z `ProvideAssembly`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
