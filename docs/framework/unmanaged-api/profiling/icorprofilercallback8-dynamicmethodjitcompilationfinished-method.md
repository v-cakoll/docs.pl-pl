---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136583"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationFinished Metoda
[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]  
  
Powiadamia profiler za każdym razem, gdy kompilacja JIT metody dynamicznej została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.   

[in] `hrStatus`   
Wartość wskazująca, czy kompilacja JIT zakończyła się pomyślnie.

[in] `fIsSafeToBlock`   
`true` wskazujący, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false` wskazujący, że blokowanie nie ma wpływu na działanie środowiska uruchomieniowego.  

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest wyzwalane za każdym razem, gdy kompilacja JIT metody dynamicznej została zakończona. Obejmuje to różne metody pośredniczące IL i LCG. Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.

> [!NOTE]
> wartości `functionId` nie można użyć do rozpoznania swoich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
