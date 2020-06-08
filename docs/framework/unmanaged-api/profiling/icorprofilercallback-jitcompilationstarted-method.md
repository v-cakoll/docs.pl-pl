---
title: ICorProfilerCallback::JITCompilationStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500042"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted — Metoda
Powiadamia program profilujący, że kompilator just in Time (JIT) rozpoczął Kompilowanie funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, dla której rozpoczyna się kompilacja.  
  
 `fIsSafeToBlock`  
 podczas Wartość wskazująca, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego. Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe poczeka na zwrócenie przez wątek wywołujący z tego wywołania zwrotnego; w przeciwnym razie `false` .  
  
 Chociaż wartość `true` nie będzie szkodliwa dla środowiska uruchomieniowego, może pochylić wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość otrzymywania więcej niż jednej pary `JITCompilationStarted` i [ICorProfilerCallback:: JITCompilationFinished —](icorprofilercallback-jitcompilationfinished-method.md) wywołań dla każdej funkcji ze względu na sposób, w jaki środowisko uruchomieniowe obsługuje konstruktory klas. Na przykład środowisko uruchomieniowe zaczyna się od JIT-Kompiluj metodę A, ale Konstruktor klasy dla klasy B musi być uruchomiony. W związku z tym kompilator JIT środowiska uruchomieniowego kompiluje Konstruktor dla klasy B i uruchamia go. Gdy Konstruktor jest uruchomiony, wywołuje metodę A, która powoduje ponowną kompilację w trybie JIT. W tym scenariuszu pierwsza kompilacja JIT metody A jest zatrzymywana. Jednak obie próby JIT-Kompiluj metodę A są raportowane przy użyciu zdarzeń kompilacji JIT. Jeśli profiler zamierza zastąpić kod języka pośredniego firmy Microsoft (MSIL) dla metody A przez wywołanie metody [ICorProfilerInfo:: SetILFunctionBody —](icorprofilerinfo-setilfunctionbody-method.md) , musi to zrobić dla obu `JITCompilationStarted` zdarzeń, ale może użyć tego samego bloku MSIL dla obu tych elementów.  
  
 Profilowani muszą obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, gdy dwa wątki jednocześnie generują wywołania zwrotne. Na przykład wątek A wywołuje `JITCompilationStarted` . Jednak przed wywołaniem wątku `JITCompilationFinished` wątek B wywołuje [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER —](icorprofilercallback-exceptionsearchfunctionenter-method.md) z identyfikatorem funkcji z `JITCompilationStarted` wywołania zwrotnego wątku a. Może się wydawać, że identyfikator funkcji nie powinien jeszcze być prawidłowy, ponieważ wywołanie `JITCompilationFinished` nie zostało jeszcze odebrane przez profiler. Jednak w przypadku takiej sytuacji identyfikator funkcji jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
- [JITCompilationFinished, metoda](icorprofilercallback-jitcompilationfinished-method.md)
