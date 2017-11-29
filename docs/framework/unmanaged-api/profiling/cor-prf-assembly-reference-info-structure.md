---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 000a338400efa0d70e690f585518304a8b525346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a>Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Udostępnia środowisko uruchomieniowe języka wspólnego z informacjami dotyczącymi odwołania do zestawu, do którego on należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Wskaźnik do publicznego klucza lub tokenu zestawu.|  
|`cbPublicKeyOrToken`|Liczba bajtów w klucza publicznego lub na tokenie.|  
|`szName`|Nazwa zestawu, do którego istnieje odwołanie.|  
|`pMetaData`|Wskaźnik do metadanych zestawu.|  
|`pbHashValue`|Wskaźnik do wyznaczania wartości skrótu dużego obiektu binarnego (BLOB).|  
|`cbHashValue`|Liczba bajtów w obiektu BLOB generowania skrótu.|  
|`dwAssemblyRefFlags`|Flagi zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_EX_CLAUSE_INFO` Struktury jest wypełniana profilera podczas deklaruje on odwołania do zestawów dodatkowe, które środowisko uruchomieniowe języka wspólnego należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.  
  
 Jeśli rejestruje profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego środowiska uruchomieniowego przekazuje ścieżkę i nazwę zestawu do załadowania wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody. Profiler może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego planuje odwoływać się z zestawu określonego w [ ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [Metoda GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [Metoda AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
