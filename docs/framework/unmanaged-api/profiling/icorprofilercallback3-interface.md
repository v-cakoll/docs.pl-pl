---
title: ICorProfilerCallback3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865574"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3 — Interfejs
Zapewnia metody wywołania zwrotnego, które są używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji o stanie dołączania i odłączania do profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[InitializeForAttach, metoda](icorprofilercallback3-initializeforattach-method.md)|Wywoływane przez środowisko CLR, aby dać profilerowi możliwość zainicjowania stanu po operacji Attach.|  
|[ProfilerAttachComplete, metoda](icorprofilercallback3-profilerattachcomplete-method.md)|Wywoływane przez środowisko CLR, aby wskazać, że profiler może teraz wywoływać metody przechwytywania.|  
|[ProfilerDetachSucceeded, metoda](icorprofilercallback3-profilerdetachsucceeded-method.md)|Powiadamia program profilujący, że aparat plików wykonywalnych języka wspólnego (CLR) ma zwolnić plik DLL profilera.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2, interfejs](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
