---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: ac7ddeed5694ad0ae6ef3d4a11fcb1fb23755b8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123228"
---
# <a name="cor_prf_assembly_reference_info-structure"></a>Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zapewnia środowisko uruchomieniowe języka wspólnego z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.  
  
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
|`pbPublicKeyOrToken`|Wskaźnik do klucza publicznego lub tokenu zestawu.|  
|`cbPublicKeyOrToken`|Liczba bajtów w kluczu publicznym lub tokenie.|  
|`szName`|Nazwa zestawu, do którego istnieje odwołanie.|  
|`pMetaData`|Wskaźnik do metadanych zestawu.|  
|`pbHashValue`|Wskaźnik do binarnego dużego obiektu typu hash (BLOB).|  
|`cbHashValue`|Liczba bajtów w obiekcie BLOB mieszania.|  
|`dwAssemblyRefFlags`|Flagi zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura `COR_PRF_EX_CLAUSE_INFO` jest wypełniana przez profiler, gdy deklaruje dodatkowe odwołania do zestawu, że środowisko uruchomieniowe języka wspólnego należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.  
  
 Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt interfejsu do tej metody. Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w [ICorProfilerCallback6:: ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)Wywołanie zwrotne GetAssemblyReferences.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [GetAssemblyReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
