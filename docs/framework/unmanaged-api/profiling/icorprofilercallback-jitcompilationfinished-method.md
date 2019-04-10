---
title: ICorProfilerCallback::JITCompilationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1abc4dd209581c9f7c8e950ea1addc74c611d248
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226061"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a>ICorProfilerCallback::JITCompilationFinished — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) została zakończona, kompilowania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, który został skompilowany.  
  
 `hrStatus`  
 [in] Wartość wskazująca, czy kompilacja zakończyła się powodzeniem.  
  
 `fIsSafeToBlock`  
 [in] Wartość do programu profilującego wskazującą, czy blokowanie wpłynie na funkcjonowanie środowiska uruchomieniowego. Wartość jest `true` Jeśli blokowanie może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; w przeciwnym razie `false`.  
  
 Mimo, że wartość `true` nie uszkodzi środowiska uruchomieniowego, jego pochylanie wyniki profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [JITCompilationStarted, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
