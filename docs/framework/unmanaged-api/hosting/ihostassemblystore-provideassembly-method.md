---
title: IHostAssemblyStore::ProvideAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5fab4ef0d67ab6b86510bd4b2f814d9456213fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763993"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly — Metoda
Pobiera odwołanie do zestawu, który nie odwołuje się [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwrócone z [ihostassemblymanager::getnonhoststoreassemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `ProvideAssembly` dla każdego zestawu, który nie jest widoczna na liście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [in] Wskaźnik do [assemblybindinfo —](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) wystąpieniu, używany przez hosta do ustalenia niektórych parametrów powiązania, w tym obecność lub brak żadnych zasad przechowywania wersji i zestawu, które można powiązać.  
  
 `pAssemblyId`  
 [out] Wskaźnik na unikatowy identyfikator dla żądanego zestawu, w tym `IStream`.  
  
 `pHostContext`  
 [out] Wskaźnik do dane specyficzne dla hosta, który służy do określania dowód żądany zestaw bez konieczności platformy wywołania wywołania. `pHostContext` odnosi się do <xref:System.Reflection.Assembly.HostContext%2A> właściwość zarządzaną <xref:System.Reflection.Assembly> klasy.  
  
 `ppStmAssemblyImage`  
 [out] Wskaźnik na adres `IStream` zawierający obraz przenośny plik wykonywalny (PE), aby zostać załadowane, lub wartość null, jeśli nie można odnaleźć zestawu.  
  
 `ppStmPDB`  
 [out] Wskaźnik na adres `IStream` który zawiera informacje o debugowaniu (PDB) programu, lub wartość null, jeśli nie można odnaleźć pliku .pdb.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Nie można odnaleźć żądanego zestawu.|  
|E_NOT_SUFFICIENT_BUFFER|Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży, aby pomieścić identyfikator, który chce hosta, aby zwrócić.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość tożsamości dla `pAssemblyId` określonej przez hosta. Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu. Środowisko CLR używa tej wartości jako unikatowy identyfikator dla strumienia. Sprawdza każdej wartości w odniesieniu do wartości dla `pAssemblyId` zwracane przez inne wywołania do `ProvideAssembly`. Jeśli host zwraca takie same `pAssemblyId` wartość dla innego `IStream`, środowisko CLR sprawdza, czy zawartość strumieniu ma już zamapowana. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast nowe mapowanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
