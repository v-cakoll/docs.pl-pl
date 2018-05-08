---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished — metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished — metoda
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia profilera, gdy kompilacja JIT dynamicznej metody została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.   

[in] `hrStatus`   
Wartość, która wskazuje, czy kompilacja JIT zakończyła się powodzeniem.

[in] `fIsSafeToBlock`   
`true` Aby wskazać, że blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.  

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest zawsze wyzwalane, gdy kompilacja JIT dynamicznej metody została ukończona. W tym różnych klas zastępczych IL i LCG metody. Jego celem jest zapewnienie autorów profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.

> [!NOTE]
> `functionId` wartości nie może służyć do rozwiązania do tokenów metadanych, ponieważ metadanych nie ma metody dynamiczne.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [DynamicMethodJITCompilationStarted — metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [Interfejs ICorProfilerCallback8](icorprofilercallback8-interface.md)
