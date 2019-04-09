---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fa1cc05ee583cf1bd59235fcd9821d1c92d21f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101435"
---
# <a name="corprfassemblyreferenceinfo-structure"></a>Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Udostępnia środowisko uruchomieniowe języka wspólnego z informacjami dotyczącymi odwołania do zestawu, należy rozważyć, podczas przeszukiwania zamknięcia odwołanie do zestawu.  
  
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
|`cbPublicKeyOrToken`|Liczba bajtów w tokenu lub klucza publicznego.|  
|`szName`|Nazwa zestawu, do którego istnieje odwołanie.|  
|`pMetaData`|Wskaźnik do metadanych zestawu.|  
|`pbHashValue`|Wskaźnik do wyznaczania wartości skrótu duży obiekt binarny (BLOB).|  
|`cbHashValue`|Liczba bajtów skrótu obiektu BLOB.|  
|`dwAssemblyRefFlags`|Flagi zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_EX_CLAUSE_INFO` Struktury jest wypełniana przez profiler, gdy deklaruje odwołań do zestawu dodatkowe środowiska uruchomieniowego języka wspólnego należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu.  
  
 Jeśli program profilujący rejestruje [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego, środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu do załadowania, wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody. Program profilujący może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego, firma planuje odwoływać się z zestawu określonego w [ ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — Struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [GetAssemblyReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
