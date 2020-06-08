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
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499080"
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
podczas`functionId`  
Identyfikator funkcji w pamięci, dla której uruchomiono kompilację JIT.

[w] `hrStatus` Wartość wskazująca, czy kompilacja JIT zakończyła się pomyślnie.

[w] `fIsSafeToBlock` 
 `true` Aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe będzie oczekiwać na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; `false`, aby wskazać, że blokowanie nie wpłynie na działanie środowiska uruchomieniowego.  

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest wyzwalane za każdym razem, gdy kompilacja JIT metody dynamicznej została zakończona. Obejmuje to różne metody pośredniczące IL i LCG. Celem jest zapewnienie autorom profilera wystarczającej ilości informacji do zidentyfikowania skompilowanej metody dla użytkowników.

> [!NOTE]
> `functionId`wartości nie można użyć do rozpoznania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
