---
title: "ICorProfilerCallback::JITCompilationStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a25f452ccb121ef7ebcae05048eb7116b4ac48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a>ICorProfilerCallback::JITCompilationStarted — Metoda
Powiadamia profilera, aby skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, dla których trwa uruchamianie kompilacji.  
  
 `fIsSafeToBlock`  
 [in] Wartość wskazującą profilera, czy blokowanie będzie miało wpływ na działanie środowiska uruchomieniowego. Wartość jest `true` Jeśli blokuje może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; w przeciwnym razie `false`.  
  
 Chociaż wartość `true` nie będzie uszkodzić środowiska uruchomieniowego, jego pochylanie wyniki profilowania.  
  
## <a name="remarks"></a>Uwagi  
 Istnieje możliwość odbierania więcej niż jedną parę `JITCompilationStarted` i [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) wywołuje dla każdej funkcji ze względu na sposób środowiska uruchomieniowego konstruktorów klas uchwytów. Na przykład środowiska uruchomieniowego rozpoczyna Metoda kompilacji JIT, ale konstruktora klasy dla klasy B musi zostać uruchomione. W związku z tym środowiska uruchomieniowego kompiluje JIT konstruktora dla klasy B i uruchamia go. Konstruktor jest uruchomiona, powoduje wywołanie do metody A, co powoduje, że metoda być ponownie kompilowane JIT. W tym scenariuszu pierwszej kompilacji JIT metody A jest zatrzymywane. Jednak zarówno próby Metoda kompilacji JIT są zgłaszane ze zdarzeń kompilacji JIT. Jeśli profilera ma zastąpić kod języka pośredniego (MSIL) firmy Microsoft dla metody A wywołując [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody, należy wykonać czynności dla obu `JITCompilationStarted` zdarzeń, ale może używać tego samego bloku MSIL dla obu.  
  
 Profilery musi obsługiwać sekwencję wywołań zwrotnych JIT w przypadkach, gdy dwa wątków jednocześnie dokonywania wywołań zwrotnych. Na przykład wywołuje wątku A `JITCompilationStarted`. Jednak przed wywołania wątku A `JITCompilationFinished`, wywołania wątku B [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) z Identyfikatorem funkcji z wątku A `JITCompilationStarted` wywołania zwrotnego. Wydaje się, że identyfikator funkcji należy jeszcze być nieprawidłowe ponieważ wywołania `JITCompilationFinished` nie ma jeszcze odebrane profilera. Jednak w przypadku takich jak ta, identyfikator funkcji jest prawidłowy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [JITCompilationFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
