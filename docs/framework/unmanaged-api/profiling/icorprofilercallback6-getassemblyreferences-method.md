---
title: Metoda ICorProfilerCallback6::GetAssemblyReferences
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc2e80d6d8207a869d43beb46cc9448bdd86dfec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>Metoda ICorProfilerCallback6::GetAssemblyReferences
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Powiadamia profilera, że zestaw w bardzo wczesny ładuje etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAssemblyPath`  
 [in] Ścieżka i nazwa zestawu, którego metadane zostaną zmodyfikowane.  
  
 `pAsmRefProvider`  
 [in] Wskaźnik do adresu [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interfejsu, który określa zestaw odwołuje się do dodania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane z tego wywołania zwrotnego są ignorowane.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi Maska zdarzenia podczas wywoływania metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody. Jeśli rejestruje profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metody wywołania zwrotnego środowiska uruchomieniowego przekazuje ścieżkę i nazwę zestawu do załadowania wraz ze wskaźnikiem do [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiektu interfejsu do tej metody. Profiler może wywoływać [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody z `COR_PRF_ASSEMBLY_REFERENCE_INFO` obiekt dla każdego zestawu docelowego planuje odwoływać się z zestawu określonego w `GetAssemblyReferences` Wywołanie zwrotne.  
  
 Użyj `GetAssemblyReferences` wywołania zwrotnego tylko wtedy, gdy profilera do zmodyfikowania metadanych zestawu można dodać odwołania do zestawów. (Ale należy pamiętać, że rzeczywiste zmiany metadanych zestawu jest wykonywane w [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)metody wywołania zwrotnego.) Profiler powinien implementować `GetAssemblyReferences` metody wywołania zwrotnego informują środowisko uruchomieniowe języka wspólnego (CLR) o tym, że odwołania do zestawów zostaną dodane po załadowaniu modułu.  Pomaga to zapewnić, że zestaw udostępniania decyzje przez środowisko CLR na tym etapie wczesne ważność chociaż profilera planuje później zmodyfikować odwołania do zestawu metadanych.  To uniknąć niektórych wystąpień, w których profilera zmiany metadanych powodują `SECURITY_E_INCOMPATIBLE_SHARE` błędu.  
  
 Używa profilera [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt udostępniany przez tę metodę, aby dodać odwołania do zestawów do walkera zamknięcia odwołanie do zestawu CLR.  [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) należy go używać tylko z wewnątrz tego wywołania zwrotnego. Wywołuje się [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metodę z tego wywołania zwrotnego nie powodują w metadanych zmodyfikowany, ale tylko w przeszukiwania zamknięcia odwołanie do zestawu zmodyfikowane. Profiler nadal będą musieli używać [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) obiekt, aby jawnie dodać odwołania do zestawów z poziomu [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego dla odwołujących się zestaw, nawet jeśli implementuje `GetAssemblyReferences` wywołania zwrotnego.  
  
 Profiler powinna być przygotowana do odbierania zduplikowane wywołania tego wywołania zwrotnego dla tego samego zestawu i powinny odpowiadać tak samo dla każdego wywołania zduplikowane (poprzez ten sam zestaw [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) wywołania).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback6, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [COR_PRF_ASSEMBLY_REFERENCE_INFO, struktura](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)  
 [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
