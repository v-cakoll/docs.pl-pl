---
title: "IHostAssemblyStore::ProvideAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2097c1ea64e5e9a2a09e0ec57243624b05eeea65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostassemblystoreprovideassembly-method"></a>IHostAssemblyStore::ProvideAssembly — Metoda
Pobiera odwołanie do zestawu, który nie jest wywoływany przez [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) zwracanego z [IHostAssemblyManager::GetNonHostStoreAssemblies](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md). Środowisko uruchomieniowe języka wspólnego (CLR) wywołuje `ProvideAssembly` dla każdego zestawu, który nie ma na liście.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBindInfo`  
 [in] Wskaźnik do [AssemblyBindInfo](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md) wystąpienia używanego przez hosta w celu ustalenia niektórych parametrów powiązania, w tym obecności lub braku dowolne zasady przechowywania wersji i które zestawu do powiązania.  
  
 `pAssemblyId`  
 [out] Wskaźnik do Unikatowy identyfikator dla żądanego zestawu dla tego `IStream`.  
  
 `pHostContext`  
 [out] Wskaźnik do dane specyficzne dla hosta, który służy do określania dowody żądany zestaw bez konieczności platformy wywołania wywołania. `pHostContext`odpowiada <xref:System.Reflection.Assembly.HostContext%2A> właściwości zarządzanej <xref:System.Reflection.Assembly> klasy.  
  
 `ppStmAssemblyImage`  
 [out] Wskaźnik do adresu `IStream` zawierający obraz przenośny plik wykonywalny (PE), który można załadować lub wartość null, jeśli nie można odnaleźć zestawu.  
  
 `ppStmPDB`  
 [out] Wskaźnik do adresu `IStream` zawierający informacje o debugowaniu (PDB) program, lub wartość null, jeśli nie można odnaleźć pliku PDB.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ProvideAssembly`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|COR_E_FILENOTFOUND (0X80070002)|Nie można zlokalizować żądanego zestawu.|  
|E_NOT_SUFFICIENT_BUFFER|Rozmiar buforu określony przez `pAssemblyId` nie jest wystarczająco duży do przechowywania identyfikator, który chce zwracać hosta.|  
  
## <a name="remarks"></a>Uwagi  
 Zwracane wartości tożsamości dla `pAssemblyId` jest określana przez hosta. Identyfikatory muszą być unikatowe w obrębie okres istnienia procesu. Środowisko CLR używa tej wartości jako unikatowy identyfikator dla tego strumienia. Sprawdza każdej wartości z wartościami dla `pAssemblyId` zwrócony przez inne wywołania `ProvideAssembly`. Jeśli host zwraca takie same `pAssemblyId` wartość dla innej `IStream`, CLR sprawdza, czy zawartość strumieniu już zostały zamapowane. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię obrazu zamiast nowego mapowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
