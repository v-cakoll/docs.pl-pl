---
title: Metoda ICorProfilerCallback6::GetAssemblyReferences
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: d15f1b568c50cf4fca28966f94a6a4becf59e734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141624"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>Metoda ICorProfilerCallback6::GetAssemblyReferences
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 podczas Ścieżka i nazwa zestawu, którego metadane zostaną zmodyfikowane.  
  
 `pAsmRefProvider`  
 podczas Wskaźnik do adresu interfejsu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) , który określa odwołania do zestawu do dodania.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwracane wartości z tego wywołania zwrotnego są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) . Jeśli Profiler rejestruje metodę wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu, który ma być załadowany, wraz ze wskaźnikiem do obiektu interfejsu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) do tej metody. Profiler może następnie wywołać metodę [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z obiektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w `GetAssemblyReferences` wywołania zwrotnego.  
  
 Użyj wywołania zwrotnego `GetAssemblyReferences` tylko wtedy, gdy profiler musi zmodyfikować metadane zestawu, aby dodać odwołania do zestawu. (Należy zauważyć, że rzeczywista modyfikacja metadanych zestawu jest wykonywana w metodzie wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)). Profiler powinien zaimplementować metodę wywołania zwrotnego `GetAssemblyReferences`, aby poinformować środowisko uruchomieniowe języka wspólnego (CLR) o tym, że odwołania do zestawów zostaną dodane po załadowaniu modułu.  Pozwala to zagwarantować, że decyzje dotyczące udostępniania zestawu wykonane przez środowisko CLR w trakcie tego wczesnego etapu pozostają prawidłowe, mimo że program profilujący planuje później zmodyfikować odwołania do zestawu metadanych.  Może to uniknąć niektórych wystąpień, w których modyfikacje metadanych profilera powodują wystąpienie błędu `SECURITY_E_INCOMPATIBLE_SHARE`.  
  
 Profiler używa obiektu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) dostarczonego przez tę metodę, aby dodać odwołania do zestawu do analizatora zamknięcia odwołań do zestawu CLR.  Obiekt [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) powinien być używany tylko w ramach tego wywołania zwrotnego. Wywołania metody [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z tego wywołania zwrotnego nie powodują zmodyfikowanych metadanych, ale tylko w zmodyfikowanym zamknięciu odwołań do zestawu. Profiler nadal będzie musiał używać obiektu [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) , aby jawnie dodawać odwołania do zestawów z poziomu wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) dla zestawu, który odwołuje się, nawet jeśli implementuje wywołanie zwrotne `GetAssemblyReferences`.  
  
 Profiler powinien zostać przygotowany do odbierania zduplikowanych wywołań tego wywołania zwrotnego dla tego samego zestawu i powinien odpowiadać identycznie dla każdego takiego duplikatu wywołania (przez nadanie tego samego zestawu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
