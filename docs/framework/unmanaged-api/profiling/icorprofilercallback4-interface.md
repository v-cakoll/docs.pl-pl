---
title: ICorProfilerCallback4 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 1b85c48859ac29738347d112dd0466a76bfdfd2c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865340"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 — Interfejs
Zapewnia metody wywołania zwrotnego, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReJITParameters, metoda](icorprofilercallback4-getrejitparameters-method.md)|Umożliwia programowi Code Profiler Ustawianie alternatywnych flag generowania kodu dla nowej rekompilowanej treści metody.|  
|[MovedReferences2, metoda](icorprofilercallback4-movedreferences2-method.md)|Raportuje nowy układ obiektów w stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.|  
|[ReJITCompilationFinished, metoda](icorprofilercallback4-rejitcompilationfinished-method.md)|Powiadamia profiler, że kompilator just-in-Time (JIT) zakończył ponowną kompilację funkcji.|  
|[ReJITCompilationStarted, metoda](icorprofilercallback4-rejitcompilationstarted-method.md)|Powiadamia profiler, że został uruchomiony kompilator just-in-Time (JIT), aby ponownie skompilować funkcję.|  
|[ReJITError, metoda](icorprofilercallback4-rejiterror-method.md)|Zgłasza błąd podczas przetwarzania żądania ponownego kompilowania.|  
|[SurvivingReferences2, metoda](icorprofilercallback4-survivingreferences2-method.md)|Raportuje układ obiektów w stercie w wyniku niekompaktowego wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
