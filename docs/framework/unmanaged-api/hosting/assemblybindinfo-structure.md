---
title: AssemblyBindInfo — Struktura
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0247f356bfc9f354edc420ea5460da02b17ab116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561143"
---
# <a name="assemblybindinfo-structure"></a>AssemblyBindInfo — Struktura
Zawiera szczegółowe informacje o zestawie, do którego istnieje odwołanie.  
  
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
|`dwAppDomainId`|Unikatowy identyfikator `IStream` zwracany przez wywołanie [ihostassemblystore::provideassembly —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md), z którym przywoływany zestaw ma być załadowany.|  
|`lpReferencedIdentity`|Unikatowy identyfikator dla przywoływanego zestawu.|  
|`lpPostPolicyIdentity`|Identyfikator przywoływanego zestawu po zastosowaniu dowolnej wartości zasad wiązania.|  
|`ePolicyLevel`|Jedną z [epolicyaction —](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) wartości, które wskazują, które zasady przechowywania wersji, powinny być stosowane do przywoływanego zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Host dostarcza Unikatowy identyfikator `dwAppDomainId` na środowisko uruchomieniowe języka wspólnego (CLR). Po wywołaniu `IHostAssemblyStore::ProvideAssembly` zwróci wartość, środowisko wykonawcze używa identyfikatora do określenia, czy zawartość `IStream` zostały zamapowane. Jeśli tak, środowisko uruchomieniowe ładuje istniejącą kopię, a nie ponowne mapowanie strumienia. Środowisko wykonawcze używa również identyfikatorem jako klucz wyszukiwania dla strumieni zwrócony z wywołania [ihostassemblystore::providemodule —](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md). W związku z tym identyfikator musi być unikatowa, żądań modułu i żądań zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
- [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
- [ModuleBindInfo, struktura](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)
