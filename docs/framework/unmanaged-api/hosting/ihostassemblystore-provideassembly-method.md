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
ms.openlocfilehash: a93d700c9c398076d87156cd2eb9c6d0d08cccfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124488"
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly — Metoda
Pobiera odwołanie do zestawu, który nie jest przywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , który jest zwracany z [IHostAssemblyManager:: GetNonHostStoreAssemblies —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Wywołania środowiska uruchomieniowego języka wspólnego (CLR) `ProvideAssembly` dla każdego zestawu, który nie znajduje się na liście.  
  
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
 podczas Wskaźnik do wystąpienia [AssemblyBindInfo —](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) , który jest używany przez hosta w celu określenia niektórych charakterystyk powiązań, w tym obecności lub braku jakichkolwiek zasad dotyczących wersji oraz zestawu, z którym ma zostać utworzone powiązanie.  
  
 `pAssemblyId`  
 określoną Wskaźnik do unikatowego identyfikatora żądanego zestawu dla tego `IStream`.  
  
 `pHostContext`  
 określoną Wskaźnik do danych specyficznych dla hosta, który jest używany do określenia dowodu żądanego zestawu bez konieczności wywołania wywołania platformy. `pHostContext` odpowiada właściwości <xref:System.Reflection.Assembly.HostContext%2A> klasy zarządzanej <xref:System.Reflection.Assembly>.  
  
 `ppStmAssemblyImage`  
 określoną Wskaźnik do adresu `IStream`, który zawiera obraz przenośnego pliku wykonywalnego (PE), który ma zostać załadowany lub ma wartość null, jeśli nie można znaleźć zestawu.  
  
 `ppStmPDB`  
 określoną Wskaźnik na adres `IStream`, który zawiera informacje o debugowaniu programu (PDB), lub wartość null, jeśli nie można znaleźć pliku. pdb.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0x80070002)|Nie można zlokalizować żądanego zestawu.|  
|E_NOT_SUFFICIENT_BUFFER|Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży, aby pomieścić identyfikator, który chce zwrócić host.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość tożsamości zwrócona dla `pAssemblyId` jest określona przez hosta. Identyfikatory muszą być unikatowe w okresie istnienia procesu. Środowisko CLR używa tej wartości jako unikatowego identyfikatora strumienia. Sprawdza każdą wartość w odniesieniu do wartości `pAssemblyId` zwracanych przez inne wywołania do `ProvideAssembly`. Jeśli host zwróci tę samą `pAssemblyId` wartość dla innego `IStream`, środowisko CLR sprawdzi, czy zawartość tego strumienia została już zamapowana. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast mapowania nowej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
