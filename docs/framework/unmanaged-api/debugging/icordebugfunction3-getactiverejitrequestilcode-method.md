---
title: Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 70a55b833acb7fa946c694a63e1e8b51562938bc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777730"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Pobiera wskaźnik interfejsu do [ICorDebugILCode](icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Wskaźnik do IL z aktywnego żądania ReJIT.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda reprezentowana przez ten obiekt `ICorDebugFunction3` ma aktywne żądanie ReJIT, `ppReJitedILCode` zwraca wskaźnik do jego IL. Jeśli nie ma aktywnych żądań, które są typowym przypadkiem, `ppReJitedILCode` ma **wartość null**.  
  
 Żądanie ReJIT jest uaktywniane tuż po powrocie wykonania z wywołania metody [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . Może nie być jeszcze skompilowana w trybie JIT, a wątki nadal mogą być wykonywane w pierwotnej wersji kodu. Żądanie ReJIT stanie się nieaktywne w trakcie wywołania profilera do metody [ICorProfilerInfo4:: RequestRevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) . Nawet po przywróceniu kodu IL wątek nadal może być wykonywany w kodzie JIT-rekompilowanym (ReJIT).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugFunction3, interfejs](icordebugfunction3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [ReJIT: Przewodnik po poradniku](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
