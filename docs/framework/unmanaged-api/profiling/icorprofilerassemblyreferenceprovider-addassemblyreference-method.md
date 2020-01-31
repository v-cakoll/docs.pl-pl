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
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866731"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a>Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Informuje środowisko uruchomieniowe języka wspólnego (CLR) odwołania do zestawu, które program Profiler ma dodać do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a>Parametry

- `pAssemblyRefInfo`

  Wskaźnik do struktury [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) , która dostarcza środowisko CLR z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.
  
## <a name="remarks"></a>Uwagi  
 Profiler wywołuje tę metodę dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w `wszAssemblyPath` argument wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) . Obiekt interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) jest przesyłany do wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , wraz ze ścieżką i nazwą zestawu w argumencie `wszAssemblyPath`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerAssemblyReferenceProvider, interfejs](icorprofilerassemblyreferenceprovider-interface.md)
- [GetAssemblyReferences, metoda](icorprofilercallback6-getassemblyreferences-method.md)
- [ModuleLoadFinished, metoda](icorprofilercallback-moduleloadfinished-method.md)
