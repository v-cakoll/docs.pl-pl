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
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430107"
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
 podczas `ModuleID`, w którym podjęto próbę ponownej kompilacji.  
  
 `methodId`  
 podczas `MethodDef` metody, w której podjęto próbę ponownej kompilacji.  
  
 `functionId`  
 podczas Wystąpienie funkcji, które jest ponownie kompilowane lub oznaczone do ponownej kompilacji. Ta wartość może być `NULL`, jeśli wystąpił błąd w poszczególnych metodach, a nie na podstawie poszczególnych wystąpień (na przykład jeśli Profiler określił nieprawidłowy token metadanych dla metody do ponownego skompilowania).  
  
 `hrStatus`  
 podczas WYNIK HRESULT wskazujący charakter błędu. Zapoznaj się z sekcją stan HRESULTs, aby zapoznać się z listą wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwracane wartości z tego wywołania zwrotnego są ignorowane.  
  
## <a name="status-hresults"></a>Stan HRESULT  
  
|Wartość HRESULT tablicy stanu|Opis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` lub token `methodDef` jest `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit`) i nie jest obsługiwany przez tę metodę.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda jest tworzona w zestawie kolekcjonowanym i dlatego nie można jej ponownie skompilować. Należy zauważyć, że typy i funkcje zdefiniowane w kontekście bez odbicia (na przykład `List<MyCollectibleStruct>`) mogą być tworzone w zestawie kolekcjonowanym.|  
|E_OUTOFMEMORY|Za mało pamięci środowiska CLR podczas próby oznaczenia określonej metody ponownej kompilacji JIT.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład, jeśli wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci nie powiedzie się, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
