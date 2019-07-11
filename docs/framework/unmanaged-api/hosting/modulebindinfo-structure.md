---
title: ModuleBindInfo — Struktura
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e0e877402daf27c375aedddf8922e919a546ae5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781176"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo — Struktura
Zawiera szczegółowe informacje o module odwołania i zestawu, który go zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwAppDomainId`|Unikatowy identyfikator `IStream` zwracanym przez wywołanie [ihostassemblystore::providemodule —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metody, z którego ma zostać załadowany moduł odwołania.|  
|`lpAssemblyIdentity`|Unikatowy identyfikator zestawu, który zawiera odwołania modułu.|  
|`lpModuleName`|Nazwa modułu.|  
  
## <a name="remarks"></a>Uwagi  
 `ModuleBindInfo` jest przekazywany jako parametr do `IHostAssemblyStore::ProvideModule`. Host dostarcza Unikatowy identyfikator `dwAppDomainId` na środowisko uruchomieniowe języka wspólnego (CLR). Po wywołaniu [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda zwróci wartość, środowisko wykonawcze używa identyfikatora do określenia, czy zawartość `IStream` zostały zamapowane. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię, a nie ponowne mapowanie strumienia. Środowisko wykonawcze używa również identyfikatorem jako klucz wyszukiwania dla strumieni, które są zwracane z wywołania `IHostAssemblyStore::ProvideAssembly` metody. W związku z tym identyfikator musi być unikatowa dla żądań modułu, a także jak w przypadku żądań zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [AssemblyBindInfo, struktura](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
