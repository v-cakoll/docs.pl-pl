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
ms.openlocfilehash: ec6472a33c49d9345793d73ac2f78f8896dc218b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError — Metoda
Powiadamia profilera, że przy użyciu kompilatora just in time (JIT) napotkał błąd w procesie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] `ModuleID` , W którym nastąpiła próba ponownej kompilacji nie powiodło się.  
  
 `methodId`  
 [in] `MethodDef` Metody, na którym została podjęta próba ponownej kompilacji nie powiodło się.  
  
 `functionId`  
 [in] Wystąpienie funkcji, które są ponownej kompilacji lub oznaczona do ponownej kompilacji. Ta wartość może być `NULL` Jeśli błąd wystąpił na podstawie-metoda zamiast bazując na wystąpienia (na przykład, jeśli profilera określono token nieprawidłowe metadane dla metody do ponownej kompilacji).  
  
 `hrStatus`  
 [in] HRESULT, która wskazuje naturę niepowodzenia. Zobacz sekcję wyników HRESULT stan listę wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wartości zwracane z tego wywołania zwrotnego są ignorowane.  
  
## <a name="status-hresults"></a>Stan wyników HRESULT  
  
|Stan tablicy HRESULT|Opis|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Lub `methodDef` token jest `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Moduł nie został jeszcze całkowicie załadowany lub Trwa zwalnianie modułu.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Określony moduł został generowane dynamicznie (na przykład przez `Reflection.Emit`) i w związku z tym nie jest obsługiwany przez tę metodę.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Metoda zostanie uruchomiony w ramach zestawu kolekcjonowanego i dlatego nie może być ponownie kompilowane. Należy pamiętać, że typy i funkcje zdefiniowanych w kontekście innych niż odbicia (na przykład `List<MyCollectibleStruct>`) można wdrożyć do zestawu kolekcjonowanego.|  
|E_OUTOFMEMORY|CLR za mało pamięci podczas próby oznaczyć określonej metody dla kompilacji JIT.|  
|Inne|System operacyjny zwrócił błąd poza kontrolą środowiska CLR. Na przykład jeśli wystąpi błąd wywołania systemu, aby zmienić ustawienia ochrony dostępu do strony pamięci, zostanie wyświetlony błąd systemu operacyjnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
