---
title: ICorProfilerCallback4::GetReJITParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 527e48d02d5267d6ae41214686c2e8c997d85dca
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499548"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters — Metoda
Umożliwia programowi Code Profiler Ustawianie alternatywnych flag generowania kodu dla nowej rekompilowanej treści metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas Moduł, który zawiera metodę, dla której środowisko CLR wymaga parametrów ponownej kompilacji JIT.  
  
 `methodId`  
 podczas `MethodDef`Metoda, dla której środowisko CLR wymaga parametrów ponownej kompilacji JIT.  
  
 `pFunctionControl`  
 podczas Wskaźnik do interfejsu [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) , który profiler może wykorzystać, aby dostarczyć informacje o ponownej kompilacji JIT dla metody, która jest ponownie kompilowana.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wystawia `GetReJITParameters` wywołanie zwrotne, aby Profiler mógł określić parametry ponownego kompilowania danej metody. `GetReJITParameters`Wywołanie zwrotne jest wydawane tylko raz na funkcję; parametry dostarczone przez profiler stosują się do wszystkich wystąpień tej funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
- [JITCompilationStarted, metoda](icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted, metoda](icorprofilercallback4-rejitcompilationstarted-method.md)
