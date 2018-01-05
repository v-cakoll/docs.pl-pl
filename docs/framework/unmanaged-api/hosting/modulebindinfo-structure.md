---
title: "ModuleBindInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399ba2471b4dc7c5e372a56a9dcab8117068a693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo — Struktura
Zawiera szczegółowe informacje o module przywoływany i zestawu, który go zawiera.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwAppDomainId`|Unikatowy identyfikator `IStream` który jest zwracany przez wywołanie do [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) metody, z którego ma zostać załadowany moduł, do którego istnieje odwołanie.|  
|`lpAssemblyIdentity`|Unikatowy identyfikator dla zestawu, który zawiera modułu, do którego istnieje odwołanie.|  
|`lpModuleName`|Nazwa modułu do którego istnieje odwołanie.|  
  
## <a name="remarks"></a>Uwagi  
 `ModuleBindInfo`jest przekazywana jako parametr `IHostAssemblyStore::ProvideModule`. Host udostępnia unikatowy identyfikator `dwAppDomainId` się środowisko uruchomieniowe języka wspólnego (CLR). Po wywołaniu [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) metoda zwróci wartość, środowisko uruchomieniowe używa identyfikatora w celu określenia, czy zawartość `IStream` zostały zamapowane. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia. Środowisko uruchomieniowe również używa tego identyfikatora jako klucz wyszukiwania dla strumieni, które są zwracane z wywołań `IHostAssemblyStore::ProvideAssembly` metody. W związku z tym identyfikatorem musi być unikatowa dla żądań modułu również podobnie jak w przypadku żądań zestawów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [AssemblyBindInfo, struktura](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
