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
ms.openlocfilehash: 31be0525c637e50c1161129277d651b56dadfaa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006769"
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo — Struktura
Zawiera szczegółowe informacje dotyczące modułu, do którego istnieje odwołanie, i zestawu, który go zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`dwAppDomainId`|Unikatowy identyfikator `IStream` , który jest zwracany przez wywołanie metody [IHostAssemblyStore::P rovidemodule](ihostassemblystore-providemodule-method.md) , z której ma zostać załadowany moduł, do którego istnieje odwołanie.|  
|`lpAssemblyIdentity`|Unikatowy identyfikator zestawu, który zawiera moduł, do którego się odwoływano.|  
|`lpModuleName`|Nazwa modułu, do którego się odwoływano.|  
  
## <a name="remarks"></a>Uwagi  
 `ModuleBindInfo`jest przenoszona jako parametr do `IHostAssemblyStore::ProvideModule` . Host dostarcza unikatowy identyfikator `dwAppDomainId` do środowiska uruchomieniowego języka wspólnego (CLR). Po wywołaniu metody [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) , środowisko uruchomieniowe użyje identyfikatora, aby określić, czy zawartość `IStream` została zamapowana. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia. Środowisko uruchomieniowe używa również tego identyfikatora jako klucza wyszukiwania dla strumieni, które są zwracane z wywołań `IHostAssemblyStore::ProvideAssembly` metody. W związku z tym identyfikator musi być unikatowy w przypadku żądań modułu, a także dla żądań zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, struktury](hosting-structures.md)
- [AssemblyBindInfo, struktura](assemblybindinfo-structure.md)
- [ICLRAssemblyIdentityManager, interfejs](iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](ihostassemblymanager-interface.md)
