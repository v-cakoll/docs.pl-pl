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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a705257c150fe0272674c08c7b316ab968766cb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475342"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>Metoda ICorProfilerCallback6::GetAssemblyReferences
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Powiadamia program profilujący, że zestaw w bardzo wczesnym ładowania etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 [in] Ścieżka i nazwa zestawu, w których metadane zostaną zmodyfikowane.  
  
 `pAsmRefProvider`  
 [in] Wskaźnik na adres [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interfejs, który określa zestaw, który odwołuje się do dodania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane to wywołanie zwrotne są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi maski zdarzenia podczas wywoływania [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody. Jeśli program profilujący rejestruje [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego, środowisko uruchomieniowe przekazuje ścieżkę i nazwę zestawu do załadowania, wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody. Program profilujący może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego, firma planuje odwoływać się z zestawu określonego w `GetAssemblyReferences` Wywołanie zwrotne.  
  
 Użyj `GetAssemblyReferences` wywołania zwrotnego, tylko wtedy, gdy program profilujący do modyfikowania metadane zestawu w celu dodania odwołania do zestawu. (Jednak należy pamiętać, że rzeczywiste zmiany dotyczące metadanych zestawu odbywa się w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)metody wywołania zwrotnego.) Program profilujący powinien implementować `GetAssemblyReferences` metody wywołania zwrotnego, środowisko uruchomieniowe języka wspólnego (CLR) poinformować, że odwołania do zestawów, zostaną dodane, gdy moduł został załadowany.  Dzięki temu zestaw udostępniania decyzje przez środowisko CLR na tym etapie wczesne zachowają ważność, mimo że profilera zamierza później zmodyfikować odwołania do zestawu metadanych.  To uniknąć pewnych okolicznościach, w której program profilujący spowodować modyfikacji metadanych `SECURITY_E_INCOMPATIBLE_SHARE` błędu.  
  
 Program profilujący używa [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt udostępniany przez tę metodę, aby dodać odwołania do zestawów do walker zamknięcia odwołania zestawów CLR.  [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu powinien można używać tylko wewnątrz tego wywołania zwrotnego. Wywołania [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z to wywołanie zwrotne nie powoduje modyfikacji metadanych, ale tylko w przypadku modyfikacji zestawu odwołania zamknięcia przeszukiwania. Program profilujący nadal będą musieli używać [imetadataassemblyemit —](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) obiektu, aby jawnie dodać odwołania do zestawów z poziomu [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego dla odwołania zestaw, nawet jeśli implementuje `GetAssemblyReferences` wywołania zwrotnego.  
  
 Program profilujący powinna być przygotowana do otrzymywać zduplikowane wywołań to wywołania zwrotnego dla tego samego zestawu, a powinien odpowiadać tak samo dla każdego wywołania zduplikowane (, wprowadzając ten sam zestaw [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) wywołania).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
