---
title: Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location: mscorwks.dll
api_type: COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f67ef9832a7fb1ff1ec153a4f8aff74079e3b76c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Informuje o środowisko uruchomieniowe języka wspólnego (CLR) z odwołania do zestawu, który profilera zamierza dodatek [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pAssemblyRefInfo  
 Wskaźnik do [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) strukturę, która dostarcza informacji na temat odwołania do zestawu, do którego on należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu CLR.  
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje tę metodę dla każdego zestawu docelowego planuje odwoływać się z zestawu określonego w `wszAssemblyPath` argument [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego. [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt interfejsu jest przekazywany do profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego, wraz z zestawu ścieżki i nazwy w `wszAssemblyPath` argumentu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [Metoda GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [ModuleLoadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
