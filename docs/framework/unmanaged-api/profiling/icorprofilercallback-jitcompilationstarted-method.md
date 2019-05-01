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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b75eebd8d9bf439a0317521a61c06ece3745be0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787923"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) została uruchomiona kompilować funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, dla których jest uruchamiana kompilacja.  
  
 `fIsSafeToBlock`  
 [in] Wartość do programu profilującego wskazującą, czy blokowanie wpłynie na funkcjonowanie środowiska uruchomieniowego. Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; w przeciwnym razie `false`.  
  
 Mimo, że wartość `true` nie uszkodzi środowiska uruchomieniowego, jego pochylanie wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Jest to możliwe, aby otrzymać więcej niż jedną parę `JITCompilationStarted` i [icorprofilercallback::jitcompilationfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołuje dla każdej funkcji ze względu na sposób środowisko wykonawcze obsługuje Konstruktory klasy. Na przykład środowisko uruchomieniowe rozpoczyna się skompilować wg JIT metody A, ale konstruktora klasy dla klasy B musi zostać uruchomione. W związku z tym, środowisko uruchomieniowe kompiluje JIT konstruktora dla klasy B i uruchamia go. Konstruktor jest uruchomiona, tworzy wywołanie metody A, co powoduje, że metoda ponownie być kompilowany dokładnie na czas. W tym scenariuszu pierwszy kompilację JIT metody A jest zatrzymywana. Jednak zarówno próby metoda skompilować wg JIT są zgłaszane ze zdarzeniami kompilacja JIT. Jeśli program profilujący ma zastąpić kod intermediate language (MSIL) firmy Microsoft dla metody element przez wywołanie metody [icorprofilerinfo::setilfunctionbody —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody, należy wykonać czynności dla obu `JITCompilationStarted` zdarzenia, ale mogą używać tego samego bloku MSIL dla obu przypadków.  
  
 Profilery muszą obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, w której dwa wątki jednocześnie wykorzystują wywołania zwrotne. Na przykład, wywołania wątku A `JITCompilationStarted`. Jednak przed wywołań wątku A `JITCompilationFinished`, wywołań wątku B [icorprofilercallback::exceptionsearchfunctionenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) identyfikatorem funkcji z wątku, A `JITCompilationStarted` wywołania zwrotnego. Wydaje się, że identyfikator funkcji nie powinny jeszcze być prawidłowy ponieważ wywołanie `JITCompilationFinished` nie ma jeszcze odebrane przez profiler. Jednak w przypadku podobny do tego identyfikator funkcji jest nieprawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
