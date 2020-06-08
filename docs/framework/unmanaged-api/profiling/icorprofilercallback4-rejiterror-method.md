---
title: ICorProfilerCallback4::ReJITError — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 488069f3ea16352cb7bb5e81b9a726637a7a65f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499366"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError — Metoda
Powiadamia profiler, że kompilator just in Time (JIT) napotkał błąd w procesie ponownej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas , `ModuleID` W którym wykonano próbę ponownej kompilacji.  
  
 `methodId`  
 podczas `MethodDef`Metoda, dla której podjęto próbę ponownej kompilacji.  
  
 `functionId`  
 podczas Wystąpienie funkcji, które jest ponownie kompilowane lub oznaczone do ponownej kompilacji. Ta wartość może być taka `NULL` , jeśli wystąpił błąd w poszczególnych metodach, a nie na poszczególnych wystąpieniach (na przykład jeśli Profiler określił nieprawidłowy token metadanych dla metody do ponownego skompilowania).  
  
 `hrStatus`  
 podczas WYNIK HRESULT wskazujący charakter błędu. Zapoznaj się z sekcją stan HRESULTs, aby zapoznać się z listą wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracane wartości z tego wywołania zwrotnego są ignorowane.  
  
## <a name="status-hresults"></a>Stan HRESULT  
  
|Wartość HRESULT tablicy stanu|Opis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID`Token lub `methodDef` `NULL` .|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit` ) i nie jest obsługiwany przez tę metodę.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda jest tworzona w zestawie kolekcjonowanym i dlatego nie można jej ponownie skompilować. Należy zauważyć, że typy i funkcje zdefiniowane w kontekście bez odbicia (na przykład `List<MyCollectibleStruct>` ) mogą być tworzone w zestawie kolekcjonowanym.|  
|E_OUTOFMEMORY|Za mało pamięci środowiska CLR podczas próby oznaczenia określonej metody ponownej kompilacji JIT.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład, jeśli wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci nie powiedzie się, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](icorprofilercallback4-interface.md)
