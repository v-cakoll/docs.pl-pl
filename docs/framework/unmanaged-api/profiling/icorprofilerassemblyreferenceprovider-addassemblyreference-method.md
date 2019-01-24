---
title: Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 762ebbe141473277dc064b36c6229f82d348f976
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582109"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Informuje środowisko uruchomieniowe języka wspólnego (CLR) z odwołania do zestawu, który profilera zamierza dodać w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 pAssemblyRefInfo  
 Wskaźnik do [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) strukturę, która udostępnia środowisko CLR z informacjami dotyczącymi odwołania do zestawu, należy rozważyć, podczas przeszukiwania zamknięcia odwołanie do zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący wywołuje tę metodę dla każdego zestawu docelowego, firma planuje odwoływać się z zestawu określonego w `wszAssemblyPath` argument [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego. [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interfejsu obiekt jest przekazywany do profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołanie zwrotne, wraz z nazwą w i ścieżka zestawu `wszAssemblyPath` argumentu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerAssemblyReferenceProvider, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
