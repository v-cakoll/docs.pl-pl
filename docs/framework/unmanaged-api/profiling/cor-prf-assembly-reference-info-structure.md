---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 4fdc8e1074bf45de3a8ab85500a85b124ce34fa1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867337"
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
  
 Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do obiektu interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) do tej metody. Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — struktury](profiling-structures.md)
- [GetAssemblyReferences, metoda](icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference, metoda](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
