---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be32718ca392ce1712b8ce9f2e33a8f602ccb242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450144"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profiling — struktury](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [GetAssemblyReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [AddAssemblyReference, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
