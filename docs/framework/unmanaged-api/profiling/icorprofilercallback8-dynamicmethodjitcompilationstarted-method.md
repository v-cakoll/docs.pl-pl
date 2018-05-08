---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted — metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted — metoda
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia profilera, gdy kompilacja JIT metody dynamicznej została uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.   

[in] `fIsSafeToBlock`   
`true` Aby wskazać, że blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.  

[in] `pILHeader`    
Wskaźnik do pierwszego bajtu nagłówka IL w metodzie.   

[in] `cbILHeader`    
Liczba bajtów w nagłówku IL. 

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest zawsze wyzwalane, gdy jest dynamiczna Metoda kompilacji JIT. W tym różnych klas zastępczych IL i LCG metody. Jego celem jest zapewnienie autorów profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.

> [!NOTE]
> `functionId` wartości nie może służyć do rozwiązania do tokenów metadanych, ponieważ metadanych nie ma metody dynamiczne.

`pILHeader` Wskaźnika jest prawidłowy tylko podczas wywołania zwrotnego.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [DynamicMethodJITCompilationFinished — metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [Interfejs ICorProfilerCallback8](icorprofilercallback8-interface.md)
