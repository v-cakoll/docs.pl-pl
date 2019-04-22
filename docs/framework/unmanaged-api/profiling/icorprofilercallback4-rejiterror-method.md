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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f152279a21f28b54acebbf0be7c65bb73efa70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150595"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) napotkał błąd w procesie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] `ModuleID` , W której nastąpiła próba ponownej kompilacji nie powiodło się.  
  
 `methodId`  
 [in] `MethodDef` Metody, na którym została podjęta próba ponownej kompilacji nie powiodło się.  
  
 `functionId`  
 [in] Wystąpienie funkcji, które jest ponownej kompilacji lub oznaczona do ponownej kompilacji. Ta wartość może być `NULL` czy błąd wystąpił na podstawie-metoda zamiast podstawę dla wystąpienia (na przykład, jeśli program profilujący określony token nieprawidłowe metadane dla metody do ponownej kompilacji).  
  
 `hrStatus`  
 [in] Wartość HRESULT wskazującą naturę niepowodzenia. Zobacz sekcję HRESULTS stanu dla listy wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane to wywołanie zwrotne są ignorowane.  
  
## <a name="status-hresults"></a>Stan HRESULTS  
  
|Stan macierzy HRESULT|Opis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Lub `methodDef` token jest `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie jest jeszcze w pełni załadowany lub jest właśnie Trwa zwalnianie.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł dynamicznie został wygenerowany (na przykład przez `Reflection.Emit`), a zatem nie jest obsługiwane przez tę metodę.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda tworzenia wystąpienia klasy w zestawie i dlatego nie może być ponownie kompilowane. Należy zauważyć, że typy i funkcje zdefiniowane w kontekście innych odbicie (na przykład `List<MyCollectibleStruct>`) można utworzyć wystąpienia w zestawie.|  
|E_OUTOFMEMORY|Środowisko CLR zabrakło pamięci w trakcie oznaczania określonej metody ponownej kompilacji JIT.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład jeśli wywołanie systemowe, aby zmienić ustawienia ochrony dostępu do strony pamięci nie powiedzie się, zostanie wyświetlony błąd systemu operacyjnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
