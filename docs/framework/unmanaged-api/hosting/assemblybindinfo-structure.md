---
title: "AssemblyBindInfo — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyBindInfo
helpviewer_keywords: AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f23c8269c7dd7f85ad0f848c1dee2ed0bf903c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo — Struktura
Zawiera szczegółowe informacje dotyczące przywoływanego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`dwAppDomainId`|Unikatowy identyfikator `IStream` zwrócony przez wywołanie do [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), z którym ma być załadowany przywoływanego zestawu.|  
|`lpReferencedIdentity`|Unikatowy identyfikator dla przywoływanego zestawu.|  
|`lpPostPolicyIdentity`|Identyfikator przywoływanego zestawu po zastosowaniu wartości zasad powiązania.|  
|`ePolicyLevel`|Jeden z [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które wskazują, które zasady przechowywania wersji, jeśli istnieje, ma zostać zastosowany do przywoływanego zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Host udostępnia unikatowy identyfikator `dwAppDomainId` się środowisko uruchomieniowe języka wspólnego (CLR). Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwraca środowiska uruchomieniowego używa identyfikatora, aby określić, czy zawartość `IStream` zostały zamapowane. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię zamiast ponownego mapowania strumienia. Środowisko uruchomieniowe również używa tego identyfikatora jako klucz wyszukiwania dla strumieni zwrócony z wywołań [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). W związku z tym identyfikator musi być unikatowy dla żądań modułu i żądań zestawów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [ICLRAssemblyIdentityManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [IHostAssemblyStore — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [ModuleBindInfo — struktura](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
