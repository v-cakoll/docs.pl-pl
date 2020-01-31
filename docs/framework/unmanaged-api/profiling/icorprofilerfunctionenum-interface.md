---
title: ICorProfilerFunctionEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: add30952588ace0cbc80191617c37d7222cffee7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864495"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum — Interfejs
Zapewnia metody sekwencyjnej iteracji przez kolekcję funkcji w środowisku uruchomieniowym języka wspólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](icorprofilerfunctionenum-clone-method.md)|Pobiera wskaźnik interfejsu do kopii tego interfejsu `ICorProfilerFunctionEnum`.|  
|[GetCount, metoda](icorprofilerfunctionenum-getcount-method.md)|Pobiera liczbę funkcji, które zostały załadowane przez aplikację lub wymuszanie załadowane przez profiler.|  
|[Next, metoda](icorprofilerfunctionenum-next-method.md)|Pobiera określoną liczbę funkcji ciągłych z sekwencyjnego zbioru funkcji, rozpoczynając od bieżącej pozycji modułu wyliczającego w sekwencji.|  
|[Reset, metoda](icorprofilerfunctionenum-reset-method.md)|Przenosi kursor modułu wyliczającego do początkowego położenia sekwencji.|  
|[Skip, metoda](icorprofilerfunctionenum-skip-method.md)|Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorProfilerFunctionEnum` jest modułem wyliczającym. Umożliwia odbiorcom tablicy ściąganie elementów od nadawcy według stawki, która jest odpowiednia dla odbiornika. Innymi słowy, odbiorca może jawnie kontrolować przepływ elementów tablicy, co pozwala uniknąć problemów związanych z przekazywaniem dużych tablic jako parametrów metody.  
  
 `ICorProfilerFunctionEnum` wylicza funkcje, które zostały już skompilowane JIT, ale nie zawierają funkcji ładowanych z obrazów natywnych generowanych za pomocą programu Ngen. exe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [EnumJITedFunctions, metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
